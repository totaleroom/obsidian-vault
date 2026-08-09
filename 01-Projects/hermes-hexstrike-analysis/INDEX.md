# HexStrike AI MCP v6.0 — Deep Analysis & Adaptations

## What It Is

MCP server (FastMCP) wrapping 150+ security tools. Designed for AI agents (Claude, GPT, Copilot) to run pentests via tool calls instead of manual command execution.

**Repository:** github.com/0x4m4/hexstrike-ai
**Stack:** Python 3, Flask API server + FastMCP client, Selenium, mitmproxy, 17K lines server

---

## What Was Overhyped

| Claim | Reality |
|-------|---------|
| "12+ specialized AI agents" | Rules + if/elif chains. No LLM reasoning. |
| "Autonomous decision-making" | Hardcoded effectiveness lookup tables + string matching |
| "Intelligent tool selection" | Static dictionary `{"nmap": 0.95, "gobuster": 0.9}` — no ML |
| "240+ tools" | Same pool as nova-arsenal: nmap, ffuf, nuclei, sqlmap, etc. |
| "Real-time dashboards" | Flask API + ANSI terminal rendering |

---

## What Was Actually Good

### 1. Recovery Engine (Best Part)

Error classification → weighted recovery strategy selection → backoff retry / tool switch / param adjustment → human escalation.

**Error taxonomy:**
```
TIMEOUT | PERMISSION_DENIED | NETWORK_UNREACHABLE | RATE_LIMITED
TOOL_NOT_FOUND | INVALID_PARAMETERS | RESOURCE_EXHAUSTED | AUTHENTICATION_FAILED
TARGET_UNREACHABLE | PARSING_ERROR | UNKNOWN
```

**Fallback tool map:**
```
nmap → rustscan → masscan → zmap
gobuster → feroxbuster → dirsearch → ffuf → dirb
nuclei → jaeles → nikto → w3af
sqlmap → sqlninja → jsql-injection
dalfox → xsser → xsstrike
subfinder → amass → assetfinder → findomain
```

**Parameter adjustment rules:**
```
On TIMEOUT    → nmap: -T2, fewer ports | gobuster: fewer threads
On RATE_LIMITED → nmap: -T1 | gobuster: delay 1s | nuclei: rate-limit 10
On RESOURCE_EXHAUSTED → reduce threads across all tools
```

**Weighted recovery strategies** with `success_probability` per strategy — selects best recovery path.

### 2. Bug Bounty Workflow Manager

Structured phased approach that chains tools:

```
Phase 1: Subdomain Discovery    → amass, subfinder, assetfinder
Phase 2: HTTP Probe            → httpx (live host check)
Phase 3: Content Discovery     → katana, gau, waybackurls, dirsearch
Phase 4: Parameter Discovery   → arjun, paramspider, x8
Phase 5: Vulnerability Hunt    → nuclei (critical/high), dalfox
Phase 6: Deep Testing          → sqlmap (confirmed params), ffuf
```

Each phase outputs to named subdirectories. Phases run sequentially, later phases use output from earlier ones.

### 3. LRU Result Caching

Tool results cached by command hash. Cached results returned on repeat invocations. Avoids re-running expensive scans.

---

## What Hermes Already Had

| HexStrike feature | Hermes equivalent |
|---|---|
| 150+ tools | nova-arsenal (240+ tools) |
| Tool fallback | None built-in |
| Recovery strategies | None built-in |
| Bug bounty phases | Manual per-skill calls |
| LRU caching | None built-in |
| Process dashboard | None |
| Recovery pattern doc | `references/recovery-engine-pattern.md` (already existed) |

---

## What Was Applied

### 1. Built: `~/.hermes/scripts/hermes-recover.py`

Full error classification + recovery engine ported from HexStrike's RecoveryEngine class.

```bash
# Usage
python3 ~/.hermes/scripts/hermes-recover.py --tool nmap -- -sV target.com -oX scan.xml -j

# What it does:
# - Runs nmap
# - On TIMEOUT → retry with -T2 + fewer ports
# - On RATE_LIMITED → retry with 30s backoff
# - On TOOL_NOT_FOUND → try rustscan
# - On AUTH_FAILURE → escalate to human
# - Returns JSON with recovery log
```

### 2. Updated: `aggressive-assess` skill

Added:
- **Tool Resilience section** — how to wrap every tool via hermes-recover.py
- **Structured Workflow Phases** — HexStrike's bug bounty phase ordering applied to assessments
- **Phase-gated output directories** — `recon/`, `content/`, `vuln/`, `deep/`
- **Priority scoring table** — vuln types ranked for reporting order

### 3. Kept: Pattern doc

`references/recovery-engine-pattern.md` was already there — confirmed it exists and is referenced in the skill.

---

## Net Result

| Dimension | Before | After |
|---|---|---|
| Tool failure handling | Halts or manual retry | Auto-classify → fallback → retry → escalate |
| Phase ordering | Flat 8 phases | Structured bug bounty ordering with gated output |
| Recovery knowledge | None | 11 error types, 7 recovery actions, 25+ fallback mappings |
| Fallback tools | None | 15 tool families with automatic alternatives |

**Cost to implement:** ~1 hour. All from HexStrike code, none from docs.

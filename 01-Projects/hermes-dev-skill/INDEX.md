# Hermes Dev Skill — Unified Development Workflow

## Overview

Single entry point for any development task in Hermes. Chains project detection, planning, TDD implementation, verification, and reporting into one skill.

**Trigger:** `/dev <project>, <feature description>`
**Skill:** `software-development/dev`

---

## The Problem It Solves

Before: 5+ separate skills for one dev task, no unified flow
- `project-memory` → detect project
- `plan` → write plan
- `test-driven-development` → build with tests
- `systematic-debugging` → fix bugs
- `requesting-code-review` → verify before commit

After: one trigger → full flow → you confirm → it ships

---

## Workflow Steps

```
Step 1: Project Detection
→ Detect project, load CLAUDE.md / context files
→ Determine project type (Node, Python, etc.)
→ Identify relevant test framework

Step 2: Context Exploration
→ Read existing code structure
→ Identify patterns, conventions, test locations
→ Map file structure

Step 3: Write Plan → STOP
→ Write plan to .hermes/plans/<timestamp>-<slug>.md
→ Show you: what will change, what files, what tests
→ Wait for: "proceed" / "yes" / "do it"

Step 4: Implement with TDD
→ Task by task, each with failing test first
→ Commit after each task
→ Use test-driven-development skill

Step 5: Pre-commit Verification
→ Run full test suite
→ Security scan (secrets, deps)
→ Code quality check

Step 6: Report
→ Summary of what was built
→ Files changed
→ How to run tests
→ Any warnings
```

---

## Example Usage

```
/dev Mantra Forge, add export-to-PDF feature for reports
/dev ~/projects/myapp, refactor auth module to use JWT
/dev current project, add rate limiting middleware
```

---

## Skill Dependencies

| Skill | Used in step |
|---|---|
| `project-memory` | Step 1-2 |
| `plan` | Step 3 |
| `test-driven-development` | Step 4 |
| `requesting-code-review` | Step 5 |
| `systematic-debugging` | Step 4 (if fixes needed) |

---

## Maintenance Log

| Date | Change |
|------|--------|
| 2026-08-09 | Created — chained existing skills into unified flow |
| 2026-08-09 | Cleaned duplicate skills (software-development/plan, test-driven-development, requesting-code-review) |
| 2026-08-09 | Restored requesting-code-review with full content from backup |

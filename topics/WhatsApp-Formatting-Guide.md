# WhatsApp Formatting Guide

**Source:** Meta / WhatsApp FAQ, community-verified
**Updated:** 2026-07-07
**Purpose:** Reference for writing human-realistic WhatsApp messages

---

## Native Formatting (Works on All Platforms)

WhatsApp has 4 native formatters — same as Discord, NOT markdown:

| Format | Syntax | Rendered | Example |
|--------|--------|----------|---------|
| **Bold** | `*text*` | bold | `*mantap*` → **mantap** |
| *Italic* | `_text_` | italic | `_mantap_` → *mantap* |
| ~~Strikethrough~~ | `~text~` | strikethrough | `~mantap~` → ~~mantap~~ |
| `Monospace` | `` `code` `` | monospace/code | `` `code` `` |

### Important Rules

- **Asterisk = bold, NOT markdown bold** — `**bold**` does NOT work on WhatsApp
- **Backtick = monospace** — triple backtick (```) renders as inline code, NOT a block
- **Underscore = italic** — spaces around the underscores are fine
- **All 4 can be combined** — `*_bold italic_*` works

### What Does NOT Work on WhatsApp

| Feature | Why |
|---------|-----|
| `# Heading` | Renders as plain text |
| `**bold**` (double asterisk) | Shows asterisks literally |
| `> blockquote` | Shows `>` character |
| `- bullet list` | Shows `-` literally |
| `` ```code block``` `` | Triple backticks render inline, not a block |
| `~~strikethrough~~` (double tilde) | Shows tildes literally |
| `**bold**` + `__underline__` | No native underline support |

### Real Typo Patterns to Avoid Looking Bot-like

| Bot Pattern | Human Pattern |
|-------------|---------------|
| Uses `**bold**` everywhere | Uses `*bold*` sparingly (max 1-2 per message) |
| Backtick monospace for everything | Uses monospace only for actual codes/numbers |
| Strikethrough for emphasis | Strikethrough feels "techy" — use rarely |
| Emoji in code blocks | Never put emoji in monospace |
| Perfect spacing around symbols | `*bold*` not `* bold *` — natural |

---

## Monospace / Code Behavior on WhatsApp

When someone types `` `text` `` on WhatsApp:
- It renders as a single-line inline code span
- No syntax highlighting
- Background is light grey, monospace font
- Does NOT create a code block (no multi-line)

For multi-line code, users typically paste plain text or use screenshots.

---

## Links & Mentions

| Feature | Syntax | Behavior |
|---------|--------|----------|
| URL auto-link | `https://...` | Auto-detected and clickable |
| Bold URL | `*[https://...]*link text*` | URL becomes clickable bold text |
| @mention | `@username` | Highlights in blue when the user exists in group |

WhatsApp does NOT support markdown link syntax `[text](url)`.

---

## Group vs DM Differences

| Feature | DM | Group |
|---------|-----|-------|
| Formatting (bold/italic/code) | ✅ works | ✅ works |
| @mention | N/A | ✅ highlights user |
| Reply to message | ✅ | ✅ |
| Forward indicator | ✅ | ✅ |
| Read receipts | ✅ | ✅ |

---

## Auto-Detection Patterns

WhatsApp auto-converts:
- `https://example.com` → clickable link
- Phone numbers → clickable tap-to-call
- Email addresses → clickable
- `*4000*` → if surrounded by spaces → bold 4000
- Date patterns like `12/12/2025` → highlighted

---

## Writing Human-Realistic Messages

### Good (Human-like)
```
Halo! Saya sudah coba *mantap* banget sih
Productnya. Cuma masih bingung soal 
`ongkir` nya, bisa dijelasin lagi?

next ya kak ↑
```

### Bad (Bot-like)
```
**PRODUCT NAME**
Harga: *Rp149.000*
• Feature 1
• Feature 2
• Feature 3
```code```
```

### Key Differences
1. **No all-caps headings** — humans rarely TYPE IN ALL CAPS on WhatsApp
2. **No bullet lists with dashes** — use natural sentences instead
3. **Short lines, line breaks for emphasis** — not for structure
4. **Sparingly bold** — humans bold things that are genuinely important
5. **`code` only for actual codes/numbers** — `021-1234`, `TRX-0001`, `KODE:ABC`
6. **No triple backticks** — use plain text line breaks instead

---

## Indonesian-Specific Patterns

Indonesian WhatsApp users commonly:
- Use `→` instead of `->` (arrow symbol)
- Use `↑` for "up" or "bawah" for "down" (reaction guidance)
- Put spaces before/after `?` and `!` when excited: `? ?`
- Repeat vowels for emphasis: `bangeet` → `bangeeet`
- Use period `.` as sentence end, not exclamation in normal tone
- Mix informal (`gue/gw`) and formal (`saya/aku`) depending on context

---

## AI Assistant Writing Rules (for Mantra AI Dashboard)

When the AI generates WhatsApp replies, it MUST follow:

1. ✅ Use `*bold*` for genuine emphasis (max 2 per message)
2. ✅ Use `_italic_` for titles, product names in context
3. ✅ Use `` `code` `` only for: order IDs, codes, prices in context
4. ✅ Line breaks for natural paragraph flow (not for lists)
5. ❌ NEVER use `**double asterisks**`
6. ❌ NEVER use markdown link syntax `[text](url)`
7. ❌ NEVER use `# headings`
8. ❌ NEVER use `> blockquotes`
9. ❌ NEVER use triple backticks for code blocks
10. ❌ NEVER use bullet list syntax `- item`
11. ❌ NEVER use `~~strikethrough~~` for emphasis
12. ❌ NEVER use emoji inside code/monospace spans
13. ✅ Use natural Indonesian casual tone (`gue/gw` vs `saya/aku` based on context)
14. ✅ Short paragraphs (1-3 sentences max)
15. ✅ `↑` or `→` for action indicators instead of arrows in code

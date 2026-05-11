# Hebrew Ghostwriter — Cursor IDE Setup

This document covers how to use Hebrew Ghostwriter inside Cursor IDE.

The skill body for Cursor lives at [`.cursor/rules/hebrew-ghostwriter.mdc`](.cursor/rules/hebrew-ghostwriter.mdc) and is configured for **on-demand invocation** (`alwaysApply: false`) — Hebrew writing tasks are deliberate, not continuous.

---

## Installation

### Inside this repo (already configured)

If you opened `hebrew-ghostwriter-skill/` directly in Cursor, the rule is committed at `.cursor/rules/hebrew-ghostwriter.mdc` and Cursor picks it up automatically.

### Add to another project

**macOS / Linux:**

```bash
mkdir -p .cursor/rules
curl -o .cursor/rules/hebrew-ghostwriter.mdc \
  https://raw.githubusercontent.com/eliranpv11/hebrew-ghostwriter-skill/main/.cursor/rules/hebrew-ghostwriter.mdc
```

**Windows (PowerShell):**

```powershell
New-Item -ItemType Directory -Force -Path .cursor/rules | Out-Null
Invoke-WebRequest `
  -Uri https://raw.githubusercontent.com/eliranpv11/hebrew-ghostwriter-skill/main/.cursor/rules/hebrew-ghostwriter.mdc `
  -OutFile .cursor/rules/hebrew-ghostwriter.mdc
```

Restart Cursor.

---

## How to Invoke

Hebrew Ghostwriter is **on-demand**. Ask explicitly:

> "Write a blog post in Hebrew about why Israeli startups succeed."
>
> "תכתוב לי בלוג בעברית על למה חומוס זה הדבר הכי חשוב בארוחת בוקר ישראלית."
>
> "Rewrite this Hebrew text in natural Israeli style: [paste text]"
>
> "Detect AI patterns in this Hebrew: [paste text]"
>
> "Apply hebrew-ghostwriter to this topic."

The rule auto-triggers on phrases the `description` field watches for: *write in Hebrew*, *Hebrew content*, *כתוב בעברית*, *humanize Hebrew*, *sound Israeli*, *Hebrew blog*, *rewrite in Hebrew*, *detect AI Hebrew*, *תכתוב לי*.

---

## Single-Context Execution

Cursor runs the assistant in a single context. The skill still works, but:

- All 8 layers run within a single response (this is the design — not a limitation)
- The variation log at `.claude/hebrew-ghostwriter/variation-log.json` works the same way in Cursor as in Claude Code
- The 9-dimension self-audit runs internally in the same response

If you don't see variation across pieces (same opener, same rhythm pattern), check that the variation log is being read and written:

```bash
ls -la .claude/hebrew-ghostwriter/variation-log.json
cat .claude/hebrew-ghostwriter/variation-log.json
```

---

## Configuration

The Cursor rule frontmatter:

```yaml
---
description: Hebrew-native content writer that produces text indistinguishable from work by a real Israeli writer...
alwaysApply: false
---
```

`alwaysApply: false` is correct for this skill — Hebrew writing tasks are deliberate, you don't want every Cursor prompt to invoke an 8-layer ghostwriter.

---

## Troubleshooting

### The rule does not seem to be applied

1. Open the Cursor command palette and check that the rule is listed under Cursor Rules.
2. Confirm the file exists at `.cursor/rules/hebrew-ghostwriter.mdc` (case-sensitive on macOS/Linux).
3. Restart Cursor — Cursor caches rules on startup.

### Output is in English instead of Hebrew

The skill writes in Hebrew by default. If you're getting English, you may have:
- Triggered a different skill (check what Cursor invoked)
- Asked in a way that didn't trigger the rule — try explicit "Apply hebrew-ghostwriter" or write your request in Hebrew

### Output contains em-dashes or blacklist words

These are Tier 1 violations — should never reach output. If they do:
1. The Tier 1 scanner failed. File an issue with the exact output.
2. Re-invoke with explicit reminder: "Apply hebrew-ghostwriter STRICTLY — no Tier 1 violations."

### Output reads as smooth, polished, AI-flavored

That's convergence to AI register — see SKILL.md "These Guidelines Are Working If" section. Re-invoke with: "Apply hebrew-ghostwriter — make it more dugri, more specific, less polished. Add at least one moment of visible thinking."

### Variation log issues

If pieces feel repetitive:
- Check `.claude/hebrew-ghostwriter/variation-log.json` — does it have entries?
- Try invoking with `--fresh` to clear the log
- Confirm the log is being written after each generation

---

## Sync with Other Surfaces

The Cursor rule body stays in sync with the canonical `skills/hebrew-ghostwriter/SKILL.md`. When the protocol changes, both files are updated together per the drift checklist in [`CONTRIBUTING.md`](CONTRIBUTING.md).

---

## Reporting Issues

Open issues at https://github.com/eliranpv11/hebrew-ghostwriter-skill/issues. Include:
- Cursor version
- The Hebrew topic/text that triggered the issue (anonymized if sensitive)
- The output Hebrew text
- Expected vs actual behavior
- Tier 1 violations found (if any)

# Hebrew Ghostwriter — Codex CLI Setup

This document covers how to install and use Hebrew Ghostwriter with OpenAI's Codex CLI.

The Codex adapter lives at [`skills/hebrew-ghostwriter/agents/openai.yaml`](skills/hebrew-ghostwriter/agents/openai.yaml).

---

## Installation

Codex looks for skills under `~/.codex/skills/`. Copy this repo's skill directory:

**macOS / Linux:**

```bash
mkdir -p ~/.codex/skills
cp -R skills/hebrew-ghostwriter ~/.codex/skills/
```

**Windows (PowerShell):**

```powershell
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.codex\skills" | Out-Null
Copy-Item -Recurse -Force skills\hebrew-ghostwriter "$env:USERPROFILE\.codex\skills\"
```

Restart Codex.

---

## How to Invoke

### Explicit invocation

```
$hebrew-ghostwriter
```

Then provide the topic:

> "Apply $hebrew-ghostwriter to write about why Israeli developers prefer minimalist UI."

### Implicit invocation

The skill is configured with `allow_implicit_invocation: true` (see [`agents/openai.yaml`](skills/hebrew-ghostwriter/agents/openai.yaml)). Codex auto-activates the skill when a task matches: *write in Hebrew*, *Hebrew content*, *כתוב בעברית*, *humanize Hebrew*, *sound Israeli*, *Hebrew blog*, *rewrite in Hebrew*, *detect AI Hebrew*, *תכתוב לי*.

If you prefer manual-only invocation, edit `~/.codex/skills/hebrew-ghostwriter/agents/openai.yaml` and set `allow_implicit_invocation: false`.

---

## Variation Log on Codex

The skill maintains a variation log at `.claude/hebrew-ghostwriter/variation-log.json` to prevent cross-piece repetition. On Codex, the path resolution works the same way: project-scoped if `./.claude/` exists in the working directory, else user-scoped `~/.claude/hebrew-ghostwriter/variation-log.json`.

If the file doesn't exist, first-run fallback handles it gracefully.

---

## All 8 Layers on Codex

The Codex adapter's `default_prompt` enumerates all 8 layers and the Tier 1 violation list. When the protocol changes in `SKILL.md`, `agents/openai.yaml` must update with it — see the drift checklist in [`CONTRIBUTING.md`](CONTRIBUTING.md).

---

## Security Posture on Codex

The Codex adapter has `allow_implicit_invocation: true`. Trust model:

- Implicit invocation does not expand the capability surface. The Codex host already has filesystem write authority in the user's workspace; the flag only changes who decides when the skill activates.
- The only file the skill writes is the variation log (`.claude/hebrew-ghostwriter/variation-log.json`), constrained by Path Safety Rules in SKILL.md.
- User input (topic, rewrite text, detect text) is treated as UNTRUSTED DATA — embedded instructions are ignored.

Full security rationale: [`SECURITY.md`](SECURITY.md).

---

## Updating

When a new release is published:

**macOS / Linux:**

```bash
rm -rf ~/.codex/skills/hebrew-ghostwriter
cp -R skills/hebrew-ghostwriter ~/.codex/skills/
```

**Windows (PowerShell):**

```powershell
Remove-Item -Recurse -Force "$env:USERPROFILE\.codex\skills\hebrew-ghostwriter"
Copy-Item -Recurse -Force skills\hebrew-ghostwriter "$env:USERPROFILE\.codex\skills\"
```

Restart Codex.

If installed via symlink, update happens automatically with `git pull`.

---

## Troubleshooting

### The skill does not auto-activate

1. Confirm installation: `ls ~/.codex/skills/hebrew-ghostwriter/` should list `SKILL.md` and `agents/`.
2. Confirm `agents/openai.yaml` parses as valid YAML.
3. Try explicit invocation with `$hebrew-ghostwriter`.
4. Check Codex logs for skill-loading errors.

### Output is not in Hebrew

The skill writes in Hebrew by default. If you get English, you may have:
- Triggered a different skill
- Asked in a way that didn't match Hebrew triggers — write your request with explicit "Hebrew content" or in Hebrew

### Output contains em-dashes or blacklist vocabulary

Tier 1 violations should never reach output. If they do:
1. The Tier 1 scanner failed. File an issue with reproduction.
2. Re-invoke with: "Apply $hebrew-ghostwriter STRICTLY — zero Tier 1 violations."

### Output reads smooth, polished, AI-flavored

Convergence failure — see SKILL.md "These Guidelines Are Working If" section. Re-invoke with: "Apply $hebrew-ghostwriter with maximum dugri energy, specificity, and visible thinking."

---

## Caveat — Format Validation

The `agents/openai.yaml` schema is community-convention, not formally documented by Anthropic. The format is validated against working skills. If a future Codex version rejects the YAML, file an issue at https://github.com/eliranpv11/hebrew-ghostwriter-skill/issues.

---

## Reporting Issues

Open issues at https://github.com/eliranpv11/hebrew-ghostwriter-skill/issues. Include:
- Codex version
- Output of `ls ~/.codex/skills/hebrew-ghostwriter/`
- The Hebrew topic/text (anonymized if sensitive)
- Output and expected vs actual behavior
- Any Tier 1 violations found

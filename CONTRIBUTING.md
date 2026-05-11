# Contributing to Hebrew Ghostwriter

Operational checklist for keeping the 8 layers consistent across files. The protocol is the contract — any change touches multiple files.

---

## Single Source of Truth

The canonical protocol lives in **[`skills/hebrew-ghostwriter/SKILL.md`](skills/hebrew-ghostwriter/SKILL.md)**.

Every other file that describes the protocol is a derivative and must stay in sync:

| File | What it derives from `SKILL.md` |
|---|---|
| [`CLAUDE.md`](CLAUDE.md) | Drop-in CLAUDE.md version — same content, no YAML frontmatter, with "merge with your project-specific CLAUDE.md" note at top |
| [`.cursor/rules/hebrew-ghostwriter.mdc`](.cursor/rules/hebrew-ghostwriter.mdc) | Cursor IDE rule — same protocol, condensed, with Cursor-specific frontmatter (`description`, `alwaysApply: false`) |
| [`skills/hebrew-ghostwriter/agents/openai.yaml`](skills/hebrew-ghostwriter/agents/openai.yaml) | Codex metadata — short description + default prompt that references the 8 layers and Tier 1 list |
| [`README.md`](README.md) | English user-facing documentation — describes the protocol but does not redefine it |
| [`README.he.md`](README.he.md) | Hebrew translation of `README.md` — must stay in sync with the English README |
| [`CHANGELOG.md`](CHANGELOG.md) | Version history. Release-note accuracy is a CPO-domain trust commitment. |
| [`SECURITY.md`](SECURITY.md) | Threat model + path safety. Update when persistence rules change. |
| [`EXAMPLES.md`](EXAMPLES.md) | Worked examples — must reference current layer numbers, current Tier 1 list, current scoring rubric |

When you change `SKILL.md`, you almost always need to change one or more of these files. The Drift Checklist below tells you which.

---

## Drift Checklist — When Changing `SKILL.md`

Run through this list every time you edit `SKILL.md`.

### When you change the 8-layer structure

- [ ] Update `CLAUDE.md` — 8-layer summary section
- [ ] Update `.cursor/rules/hebrew-ghostwriter.mdc` — 8-layer section
- [ ] Update `README.md` — "How It Works — 8 Layers" table
- [ ] Update `README.he.md` — Hebrew layers table
- [ ] Update `EXAMPLES.md` — any layer references in worked examples
- [ ] Update `skills/hebrew-ghostwriter/agents/openai.yaml` — `default_prompt` enumerates 8 layers

### When you change Tier 1 Violations (canonical list)

- [ ] Update `SKILL.md` — canonical list at top
- [ ] Update `CLAUDE.md` — Tier 1 table
- [ ] Update `.cursor/rules/hebrew-ghostwriter.mdc` — Tier 1 list
- [ ] Update `README.md` — "Tier 1 Violations — Auto-Fail" section
- [ ] Update `README.he.md` — Hebrew Tier 1 section
- [ ] Update `EXAMPLES.md` — if examples reference specific Tier 1 violations
- [ ] Update `skills/hebrew-ghostwriter/agents/openai.yaml` — Tier 1 enumeration in `default_prompt`
- [ ] Update `CHANGELOG.md` — note the Tier 1 change explicitly

### When you change the 9-dimension scoring rubric

- [ ] Update `SKILL.md` Layer 6
- [ ] Update `CLAUDE.md` Layer 6 weights table
- [ ] Update `.cursor/rules/hebrew-ghostwriter.mdc` Layer 6 reference
- [ ] Update `README.md` — Soul/scoring references in "How It Works"
- [ ] Update `README.he.md` — Hebrew equivalents
- [ ] Update `--show-score` block format in SKILL.md if weights changed

### When you change Soul Layer techniques (Layer 7)

- [ ] Update `SKILL.md` Layer 7 — the 20 techniques in 6 categories
- [ ] Update `CLAUDE.md` Layer 7 summary
- [ ] Update `.cursor/rules/hebrew-ghostwriter.mdc` Layer 7 list
- [ ] Update Soul Layer Activation Protocol table in `SKILL.md`
- [ ] Update `EXAMPLES.md` if examples reference specific Soul techniques

### When you change Versatility Engine (Layer 8)

- [ ] Update `SKILL.md` Layer 8 — fingerprint dimensions, schemas, openers, rhythms, vocab, closings
- [ ] Update Variation Fingerprint output format example
- [ ] Update `CLAUDE.md` Layer 8 summary
- [ ] Update `.cursor/rules/hebrew-ghostwriter.mdc` Layer 8 reference
- [ ] Update `SECURITY.md` if persistence format changed

### When you change flags or modes

- [ ] Update `SKILL.md` — Argument Parsing section
- [ ] Update `CLAUDE.md` — Flags table
- [ ] Update `.cursor/rules/hebrew-ghostwriter.mdc` — Flags section
- [ ] Update `README.md` — Quick Start examples
- [ ] Update `README.he.md` — Quick Start examples
- [ ] Update `EXAMPLES.md` — any example using the changed flag
- [ ] Update `skills/hebrew-ghostwriter/agents/openai.yaml` — `default_prompt` mentions of flags

### When you change the variation log path or schema

- [ ] Update `SKILL.md` Layer 8 Phase 1 — Step P1-1 and P1-7
- [ ] Update `CLAUDE.md` — Persistence section
- [ ] Update `.cursor/rules/hebrew-ghostwriter.mdc` — Persistence section
- [ ] Update `SECURITY.md` — Path Safety + variation log content section
- [ ] Update `README.md` install permissions note if applicable
- [ ] Bump minor version (this is a security-posture change)

### When you bump the version

- [ ] `skills/hebrew-ghostwriter/SKILL.md` — `metadata.version` in YAML frontmatter
- [ ] `.claude-plugin/marketplace.json` — `metadata.version` AND `plugins[0].version`
- [ ] `.claude-plugin/plugin.json` — `version`
- [ ] `README.md` — version badge URL
- [ ] `README.he.md` — version badge URL
- [ ] `CHANGELOG.md` — new entry at top with the version, date, and per-section delta

Verify with:
```bash
grep -n "version" .claude-plugin/marketplace.json .claude-plugin/plugin.json
grep "^  version:" skills/hebrew-ghostwriter/SKILL.md
grep "badge/version" README.md README.he.md
```

All should show the same version.

### When you add another language translation

To add another README language (e.g., Spanish — `README.es.md`):

1. Copy `README.md` to `README.<lang>.md` (lowercase ISO 639-1 code).
2. Translate prose. Keep code blocks, install commands, file paths, and `file:line` citations in English.
3. Add a link to the new translation at the top of `README.md` (under the existing language line).
4. Add corresponding links at the top of every other translated README pointing back to English and to sibling languages.
5. Add the new file to the file-structure listing in `README.md` and in every translation.
6. When you update `README.md` in future, update every translation in lockstep.

---

## Hebrew Content Examples Quality Bar

When adding or modifying examples in `EXAMPLES.md` or in SKILL.md sections:

1. **Real Hebrew, not Hebrew-flavored English.** The example must read as something a native Israeli could have written or said.
2. **Specific, not generic.** Use real entity names (גיל שוויד, רועי מן, פלורנטין, מאנדיי) not placeholders ("a tech entrepreneur", "a coffee shop").
3. **Include the AI tells the example is supposed to demonstrate.** If illustrating P1 (significance inflation), the AI version must actually contain significance inflation phrases.
4. **The "After" must score 95+** against the 9-dimension rubric.
5. **Hebrew direction and punctuation.** Hebrew is RTL; in mixed Hebrew-English examples, punctuation can shift. Verify rendering in GitHub before merging.

---

## Quality Bar for Protocol Changes

If you propose a change to `SKILL.md` that affects the 8-layer structure, Tier 1 list, scoring rubric, or any mandatory prohibition — open an issue first describing:

1. The user-visible problem the change solves.
2. The failure mode of the current protocol.
3. Concrete evidence (a real session output, a real user complaint, a real attack path, or a real research finding) that justifies the change.

Protocol changes without grounding will be declined. The 8 layers are the contract — opening them requires the same rigor a real ghostwriter would demand of an edit to their style guide.

---

## Research Citation Quality Bar

When citing academic research in SKILL.md or other files:

1. **Real papers only.** No invented citations. Verify against the actual paper title, year, and venue.
2. **Match the claim to the paper.** Don't cite PNAS 2025 for a claim about ivrit.ai — those are different sources.
3. **Update when better research supersedes earlier findings.** If a 2026 paper updates the 2024 baseline, swap the citation.

---

## License

By contributing, you agree your contributions are licensed under the MIT License (see [`LICENSE`](LICENSE)).

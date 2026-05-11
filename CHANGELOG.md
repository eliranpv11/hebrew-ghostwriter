# Changelog

All notable changes to the Hebrew Ghostwriter skill.

The format is loosely based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [1.0.0] — 2026-05-11

Inaugural public release.

### What this is

Hebrew Ghostwriter is a Hebrew-native content writer that produces text indistinguishable from work by a real Israeli writer. Eight layers of authenticity construction, grounded in:

- 500,000 real Israeli comments analyzed (HeBERT UGC dataset, Tel Aviv University)
- 90 million words of Israeli podcast transcripts (ivrit.ai corpus)
- 6 AI detection tools analyzed (GPTZero, Originality.ai, Turnitin, Copyleaks, ZeroGPT, Sapling)
- 10+ academic papers including DetectGPT (ICML 2023), Binoculars (ICML 2024), RAID Benchmark (ACL 2024), PNAS 2025 register-leveling, Antislop ICLR 2026, EMNLP 2025 stylometric research, Frontiers 2025 Hebrew argumentative discourse stance

### Design decisions in this release

This skill represents a content-only architecture — a focused tool for writing, rewriting, and detecting Hebrew text. The design intentionally excludes voice cloning systems (no per-author style profiles, no Key Tells extraction, no calibration loops). The tradeoff: simpler operation, lower token cost, broader applicability. Users who need persistent voice cloning across pieces should look elsewhere.

The eight layers:

1. **Hebrew Mind** — Hebrew-first thinking with 7 core principles
2. **Linguistic Precision** — Gender system with strategic imperfection, spelling variation, construct/של by register, binyanim awareness
3. **Anti-Detection Engine** — 16-word AI vocabulary blacklist, 6 content patterns (P1-P6), 10 Hebrew-specific tells, 5 Big No-Nos
4. **Israeli Voice Injection** — Dugri Principle, slang and loanword system, discourse marker injection, humor and cultural texture, emotional authenticity
5. **Rhythm and Statistical Anti-Detection** — 3-40 Rule, burstiness, perplexity injection, vocabulary diversity, n-gram breaking
6. **Self-Audit Loop** — 9-dimension weighted scoring (95/100 threshold)
7. **Soul Layer (נשמה עמוקה)** — 20 active authenticity techniques in 6 categories
8. **Versatility Engine (מנגנון המגוון)** — 5-dimension Variation Fingerprint with cross-piece memory at `.claude/hebrew-ghostwriter/variation-log.json`

### Tier 1 Violations — Auto-fail conditions

Defined as a canonical source at the top of SKILL.md. Referenced (not duplicated) by every other section:

1. Em-dash (—) anywhere in Hebrew
2. 16 blacklisted words (מגוון, מרתק, חיוני, מהותי, ייחודי, רב-ממדי, מקיף, חדשני, פורץ דרך, חסר תקדים, משמעותי, מרכזי, בולט, רלוונטי, רב-תכליתי, מאתגר)
3. More than 1 negative parallelism ("לא X אלא Y") per piece
4. Significance inflation (מהווה אבן דרך, משקף מגמה רחבה, מסמל את, מהווה נקודת מפנה, מעיד על שינוי עמוק)
5. Macro copy windup ("ויש לזה מחיר", "ופה בדיוק הבעיה", "וזה מה שמשנה", "בואו נדבר על")
6. Three or more consecutive same-length sentences (within 3 words of each other)
7. Formal connectors in casual register (לפיכך, אי לכך, יתרה מזאת, יתר על כן, על כן, משכך, הינו, כמו כן as sentence opener)

### Modes

- `generate` — write Hebrew content from scratch
- `rewrite` — extract meaning to bullets, then write fresh Hebrew (never word-for-word translation)
- `detect` — scan text and report AI patterns; diagnosis only

### Flags

```
--mode generate|rewrite|detect      Default: generate
--type blog|academic|social|business|email|creative|auto   Default: auto
--length short|medium|long|xl|NUMBER   Default: medium
--gender male|female|neutral         Default: auto-detect
--fresh                              Clear variation log
--show-score                         Append 9-dim self-audit block
```

### Multi-platform distribution

Compatible with Claude Code (CLI), Claude.ai (Web & Desktop), Cursor IDE, Codex CLI, and any agent supporting the Agent Skills open standard. Single canonical source (SKILL.md); derived files for each platform.

### Language

User-facing output is always in Hebrew. The score block, error messages, and clarification questions are produced in the user's invocation language — Hebrew for Hebrew users, English for English users.

### Documentation

- `README.md` — English entry point
- `README.he.md` — Hebrew translation
- `CLAUDE.md` — drop-in methodology for any CLAUDE.md file
- `CURSOR.md` — Cursor IDE setup
- `CODEX.md` — Codex CLI setup
- `EXAMPLES.md` — before/after worked examples
- `CONTRIBUTING.md` — drift checklist for cross-file consistency
- `SECURITY.md` — input trust boundary and persistence threat model

### Statistical data informing the rules

Real Israeli text measurements used as targets:

| Metric | Source | Skill target |
|--------|--------|--------------|
| Avg sentence length | 8.9 words (HeBERT comments) / 13.2 words (ivrit.ai speech) | 10-12 words (weighted) |
| Ellipsis (...) | 21.6% of comments / 41.4% of spoken chunks | 20-30% of paragraphs |
| נו frequency | 3.77% of all tokens (ivrit.ai) | Dominant marker in casual |
| English code-switching | 4.1% / 9.2% | 5-8% of segments |
| Self-corrections | 10.2% of segments (ivrit.ai) | ≥ 1 per 500 words |
| Top opener word | אז (4.5% of segment openers, ivrit.ai) | Natural default opener |
| דווקא | 88/5000 segments (ivrit.ai) | ~1 per 500 words |

---

## Future versions

### Tracked but not in v1.0.0

- **Optional voice cloning add-on** — if user demand emerges. Currently out of scope by design.
- **Per-piece quality dashboard** — visualization of the 9-dim scoring trend over time.
- **More content type presets** — legal, medical, technical documentation.
- **More Hebrew dialects** — Mizrahi, Sephardi vernacular variations.
- **Citation suggestion** — when the writer claims data, suggest a real source format.
- **Long-form mode** — chapter-length pieces (5,000+ words) with consistent voice across sections.

### Not planned

- **Voice cloning** — explicitly removed from scope. This skill is content-only.
- **AI detection bypass guarantee** — no skill can guarantee detector evasion across all platforms. The skill targets best-effort statistical fingerprint elimination with focus on native-reader plausibility, which is the more durable goal.
- **Generation in other languages** — Hebrew only. Cross-language generation is a different problem.

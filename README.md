# Hebrew Ghostwriter

> *Write Hebrew that passes every AI detector and fools native Israelis.
> A Hebrew-native content writer that produces text indistinguishable from work by a real Israeli writer.
> Eight layers. No voice cloning. Content only.*

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Version](https://img.shields.io/badge/version-1.0.0-green.svg)](skills/hebrew-ghostwriter/SKILL.md)
[![Claude Code](https://img.shields.io/badge/Claude_Code-Plugin-blueviolet.svg)](https://docs.anthropic.com/en/docs/claude-code)
[![Hebrew](https://img.shields.io/badge/Language-Hebrew_🇮🇱-white.svg)]()

**🇮🇱 [קרא ב-עברית — README.he.md](README.he.md)**

---

## Who This Is For

You write Hebrew content — blogs, articles, social posts, business communications — and want it to sound like a native Israeli sat down and typed it. Not translated English. Not formal textbook Hebrew. Not "AI Hebrew" that every Israeli spots in two seconds.

Real, casual, dugri Israeli Hebrew — the kind you'd read on Geektime, in a LinkedIn post from a Tel Aviv founder, or in a WhatsApp message from your team lead.

The typical user is a **content writer, marketer, blogger, or founder** who needs Hebrew output that:
- Passes GPTZero, Originality.ai, ZeroGPT, and Copyleaks at >85% human
- Reads as authentically Israeli to native readers
- Doesn't sound like a translation or a textbook

If your Hebrew content is one-off and disposable — this skill is overkill. If you're producing content others will read — this is exactly for you.

---

## What You'll Get

Hebrew text that:

1. **Avoids the 16-word AI vocabulary blacklist** — מגוון, חיוני, ייחודי, חדשני, מקיף, רב-ממדי, פורץ דרך, etc.
2. **Avoids the 6 content patterns** that flag AI to native readers (significance inflation, copula stuffing, -ing constructions, promotional language, vague attributions, formulaic challenges)
3. **Catches the 5 Big No-Nos** that survive every other humanizer — Macro Copy, Slide Structure, LinkedIn Punchline, Disconnected Temperature, X-not-Y Addiction
4. **Uses real Israeli voice** — dugri directness, slang (סבבה, תכל'ס, יאללה), discourse markers (נו, אז, בעצם, כאילו, יעני), cultural references that an Israeli would recognize
5. **Has soul** — 20 authenticity techniques across 6 categories: specificity, conviction, digression, vulnerability, non-linearity, Hebrew-specific markers (דווקא, the dugri opener, the natural stumble)
6. **Varies between pieces** — Variation Fingerprint with 5 dimensions prevents the LLM register-leveling problem (PNAS 2025)
7. **Scores ≥95/100** on internal self-audit before output

---

## How It Works — 8 Layers

| Layer | What It Does |
|-------|-------------|
| **1. Hebrew Mind** | Forces Hebrew-first thinking — no English-to-Hebrew translation |
| **2. Linguistic Precision** | Gender system with strategic imperfection, spelling variation, construct/של by register, binyanim awareness |
| **3. Anti-Detection Engine** | 16-word blacklist, 6 content patterns, 10 Hebrew-specific tells, **5 Big No-Nos** |
| **4. Israeli Voice Injection** | Dugri directness, slang system, discourse markers, humor, cultural texture |
| **5. Rhythm Engineering** | Data-driven sentence lengths (avg 10-12 words, based on 550K real Israeli texts), burstiness, perplexity, ellipsis, n-gram breaking |
| **6. Self-Audit Loop** | 9-dimension scoring (95/100 threshold), autonomous quality gate |
| **7. Soul Layer (נשמה עמוקה)** | 20 active authenticity techniques in 6 categories — what separates AI-passing text from text that reads like a real person wrote it |
| **8. Versatility Engine (מנגנון המגוון)** | 5-dimension Variation Fingerprint prevents cross-piece repetition |

---

## The Big No-Nos

Five advanced AI patterns that survive every other humanizer — this skill catches them all:

1. **Macro Feeling Copy** — "ויש לזה מחיר אמיתי:" is a drum roll, not content. Delete.
2. **Presentation Slide Structure** — Parallel stacked points pretending to be prose. Weave them into the argument.
3. **LinkedIn Punchline Syndrome** — "הפתרון הכי חכם הוא הפתרון הכי פשוט" belongs on a sunset poster, not in writing.
4. **Disconnected Temperature** — Flat emotional energy throughout. Real writers care more about some parts.
5. **"Not X, It's Y" Addiction** — The most common AI essay structure. We break it.

---

## Tier 1 Violations — Auto-Fail

Seven absolute bans. A piece scoring 98/100 with any of these fails:

1. Em-dash (—) anywhere in Hebrew
2. Any of the 16 blacklist words
3. More than 1 negative parallelism ("לא X אלא Y")
4. Significance inflation (מהווה אבן דרך, משקף מגמה רחבה, etc.)
5. Macro copy windup ("ויש לזה מחיר", "ופה בדיוק הבעיה")
6. 3+ consecutive same-length sentences
7. Formal connectors in casual register (לפיכך, אי לכך, יתר על כן)

---

## Modes

| Mode | What It Does |
|------|-------------|
| `generate` | Write from scratch. Give it a topic, get a complete piece. |
| `rewrite` | Transform existing content (Hebrew, English, or mixed) into natural Israeli Hebrew. NEVER word-for-word translation — extracts meaning, then writes fresh. |
| `detect` | Scan text and report AI patterns found. No changes — diagnosis only. |

---

## Content Types

Auto-detected or manually set with `--type`:

| Type | Register | Example |
|------|----------|---------|
| `blog` | Casual Israeli (3/10 formality) | Blog posts, LinkedIn, articles |
| `academic` | Formal with Israeli backbone (8/10) | Papers, research, academic writing |
| `social` | Maximum casual (1/10) | Twitter, Facebook, Instagram |
| `business` | Professional but Israeli (6/10) | Reports, proposals |
| `email` | Direct and terse (4/10) | Israeli business emails |
| `creative` | Adapts to story voice | Fiction, poetry, narrative |

---

## Quick Start

### Use it

```
/hebrew-ghostwriter "למה סטארטאפים ישראלים מצליחים"
```

```
/hebrew-ghostwriter "הטכנולוגיה המתקדמת מהווה גורם מכריע..." --mode rewrite
```

```
/hebrew-ghostwriter "paste your text here" --mode detect
```

```
/hebrew-ghostwriter "topic" --length long --type academic --gender female
```

```
/hebrew-ghostwriter "topic" --show-score
```

```
/hebrew-ghostwriter "topic" --fresh
```

### Language

The user-facing output is **always in Hebrew**. The score block, error messages, and clarification questions are in the language you invoked in — Hebrew for Hebrew users, English for English users.

---

## Installation — Quick Decision

| Your setup | Use |
|---|---|
| **Claude Code (CLI)** | Option A — plugin install (recommended) |
| **Claude.ai (web/desktop)** | Option B — paste into Skills |
| **Cursor IDE** | Option G — `.cursor/rules` rule |
| **Codex CLI** | Option H — bundled skill |
| **Project-scoped (share with team)** | Option D — `.claude/skills/` in repo |
| **No installer / minimal** | Option F — paste `CLAUDE.md` content |

---

## Installation Options

### Option A — Claude Code Plugin (recommended)

```
/plugin marketplace add eliranpv11/hebrew-ghostwriter-skill
/plugin install hebrew-ghostwriter@hebrew-ghostwriter
```

The skill is installed globally across all your Claude Code sessions immediately.

### Option B — Claude.ai (Web & Desktop)

1. Go to **claude.ai → Customize → Skills**
2. Click **+** → **Create skill**
3. Paste the contents of [`skills/hebrew-ghostwriter/SKILL.md`](skills/hebrew-ghostwriter/SKILL.md) into the skill editor
4. Name it `hebrew-ghostwriter` and save
5. Toggle it on

### Option C — Personal install (all your projects)

```bash
mkdir -p ~/.claude/skills
git clone https://github.com/eliranpv11/hebrew-ghostwriter-skill.git \
  ~/.claude/skills/hebrew-ghostwriter
```

### Option D — Project install (shared with team)

```bash
mkdir -p .claude/skills
git clone https://github.com/eliranpv11/hebrew-ghostwriter-skill.git \
  .claude/skills/hebrew-ghostwriter
git add .claude/skills/
git commit -m "chore: add Hebrew Ghostwriter skill"
```

### Option E — One-liner (no git required)

```bash
mkdir -p ~/.claude/skills/hebrew-ghostwriter && \
  curl -o ~/.claude/skills/hebrew-ghostwriter/SKILL.md \
  https://raw.githubusercontent.com/eliranpv11/hebrew-ghostwriter-skill/main/skills/hebrew-ghostwriter/SKILL.md
```

### Option F — CLAUDE.md paste (zero-install)

Copy the contents of [`CLAUDE.md`](CLAUDE.md) into your project's `CLAUDE.md` file.

### Option G — Cursor IDE

```bash
mkdir -p .cursor/rules
curl -o .cursor/rules/hebrew-ghostwriter.mdc \
  https://raw.githubusercontent.com/eliranpv11/hebrew-ghostwriter-skill/main/.cursor/rules/hebrew-ghostwriter.mdc
```

See [`CURSOR.md`](CURSOR.md) for full setup.

### Option H — Codex CLI

```bash
mkdir -p ~/.codex/skills
cp -R skills/hebrew-ghostwriter ~/.codex/skills/
```

See [`CODEX.md`](CODEX.md) for full setup.

---

## Verify Installation

```
Apply hebrew-ghostwriter: כתוב לי בלוג של 300 מילים על למה ישראלים אוהבים חומוס
```

You should get a 300-word Hebrew blog post that:
- Uses Israeli slang (תכל'ס, ממש, סבבה) where the casual register fits
- Includes at least one cultural reference an Israeli would recognize
- Varies sentence length — short fragments alongside longer sentences
- Has a position the writer commits to, not balanced neutrality
- Contains a דווקא move, a memory drop, or another Soul Layer technique
- Zero em-dashes, zero blacklist words

If you get a generic blurb with words like חיוני, מקיף, חדשני — the skill is not loaded.

### If the skill is not loaded

1. Run `/plugins` in Claude Code.
2. Confirm `hebrew-ghostwriter @ hebrew-ghostwriter` is in the **Installed** tab and toggled on.
3. If not listed, repeat the install (Option A above).
4. If listed but disabled, enable it and restart Claude Code.
5. Force a clean reinstall (see **Updating → Fallback** below).

---

## Research Foundation

This skill is data-grounded:

- **6 AI detection tools analyzed** — GPTZero, Originality.ai, Turnitin, Copyleaks, ZeroGPT, Sapling
- **10+ academic papers** — DetectGPT (ICML 2023), Binoculars (ICML 2024), RAID Benchmark (ACL 2024), PNAS 2025 register-leveling, Antislop ICLR 2026 (8,000+ pattern taxonomy), EMNLP 2025 stylometric research, Frontiers 2025 Hebrew argumentative discourse stance
- **500,000 real Israeli comments analyzed** — HeBERT UGC dataset (Tel Aviv University)
- **90 million words of Israeli podcast transcripts** — ivrit.ai corpus
- **Hebrew linguistics research** — Academy of Hebrew Language standards, discourse marker studies, morphological analysis

Statistical data from real Israeli text drives the rules:

| Metric | Comments (HeBERT, 500K) | Podcasts (ivrit.ai, 742K words) | Skill target |
|--------|------------------------|--------------------------------|--------------|
| Avg sentence length | 8.9 words | 13.2 words | 10-12 words (weighted) |
| Ellipsis frequency | 21.6% of chunks | 41.4% of chunks | 20-30% of paragraphs |
| נו (discourse marker) | — | 3.77% of all tokens | Heavy in casual |
| English code-switching | 4.1% | 9.2% | 5-8% of segments |
| Self-corrections | — | 10.2% of segments | ≥ 1 per 500 words |

---

## Updating

```
/plugins → Installed → hebrew-ghostwriter → Update now
```

### Fallback — force a clean reinstall

**Windows (PowerShell):**

```powershell
Remove-Item -Recurse -Force "$env:USERPROFILE\.claude\plugins\cache\hebrew-ghostwriter"
Remove-Item -Recurse -Force "$env:USERPROFILE\.claude\plugins\marketplaces\eliranpv11-hebrew-ghostwriter-skill*"
```

**macOS / Linux:**

```bash
rm -rf ~/.claude/plugins/cache/hebrew-ghostwriter
rm -rf ~/.claude/plugins/marketplaces/eliranpv11-hebrew-ghostwriter-skill*
```

Then reinstall via Option A.

---

## Compatibility

- Claude Code (CLI)
- Claude.ai (Web & Desktop)
- Cursor IDE
- Codex CLI
- Any agent supporting the Agent Skills open standard

---

## Contributing

See [`CONTRIBUTING.md`](CONTRIBUTING.md) for the drift checklist that keeps the 8 layers consistent across files.

---

## File Structure

```
hebrew-ghostwriter-skill/
├── README.md                              ← This file (English)
├── README.he.md                           ← Hebrew README
├── CLAUDE.md                              ← Drop-in for any CLAUDE.md
├── CURSOR.md                              ← Cursor IDE setup
├── CODEX.md                               ← Codex CLI setup
├── EXAMPLES.md                            ← Before/after examples
├── CONTRIBUTING.md                        ← Drift checklist
├── CHANGELOG.md                           ← Release history
├── SECURITY.md                            ← Threat model + persistence
├── LICENSE                                ← MIT
├── .claude-plugin/
│   ├── marketplace.json
│   └── plugin.json
├── skills/
│   └── hebrew-ghostwriter/
│       ├── SKILL.md                       ← The canonical 8-layer protocol
│       └── agents/
│           └── openai.yaml                ← Codex metadata
└── .cursor/
    └── rules/
        └── hebrew-ghostwriter.mdc         ← Cursor IDE rule
```

---

## Tradeoff

This skill biases toward authentic Israeli voice over universal Hebrew. For diplomatic, multinational, or non-Israeli Hebrew contexts — adjust register manually. For literary or poetic Hebrew — this skill targets prose, not verse. For minimal/throwaway Hebrew text — do not invoke.

If the output reads as smooth, polished, "professional" — that is convergence to AI register. Roughness, specificity, and dugri energy are the signs of real Hebrew. Tune for those.

---

## License

MIT — see [LICENSE](LICENSE)

# Human Writer — Spanish (es) — a Claude skill

A Claude Code skill that produces **Spanish** prose reading as human-authored, sanitizes Spanish AI drafts to remove detector tells, and scores any Spanish draft for AI-detection risk before publication.

This is the **Spanish member** of the `human-writer` per-language family — one autonomous skill per language (`en`, `fr`, `es`, `pt`, `de`, `ar`, `hi`), all built on the same architecture. They install side by side and do not conflict: each activates on its own language triggers.

## Why this skill exists

`mr-bridge.com` ships localized marketing and editorial copy in Spanish. Modern Sonnet / Opus / GPT-class Spanish output is fluent enough to ship, but it carries fingerprints that commercial detectors (Copyleaks, GPTZero, Originality.ai) latch onto, and Spanish carries its own tells the bare statistical detectors never checked:

- **Statistical:** low burstiness, narrow type-token ratio (language-agnostic).
- **Stylistic:** the same forty or fifty inflated words repeated across drafts ("cabe destacar", "sin lugar a dudas", "aprovechar", "robusto"), formulaic frames ("No se trata solo de X, sino de Y").
- **Typographic (Spanish-specific):** dropped opening `¿` / `¡` marks, Anglo spaced em-dashes "—" used where native Spanish uses commas or the dialogue raya, EN→es calques ("sin fisuras", "accionable", "librería", "remover").

A draft drops, a client runs it through a detector, the score comes back at 70%+, and it's rejected. The fix is a disciplined sweep of the specific Spanish tells detectors weight. This skill encodes that doctrine plus a deterministic analyzer so any Claude Code session can produce, clean, or audit Spanish prose to a target score before delivery.

## What it can do

**Three modes:**
- **Write (escribir):** produce new Spanish content already engineered to score LOW_RISK.
- **Clean (limpiar):** rewrite an existing Spanish AI draft to strip tells, preserving meaning.
- **Audit (auditar):** score a Spanish draft, surface the top offending tells, recommend fixes without rewriting it.

**One language, fully specialized:**
- **Spanish (es):** ~180-entry suspect vocabulary (Tier 1 + Tier 2), Spanish AI-construction regex bank, Spanish tricolon detector (`y` / `e` conjunction), and a dedicated `¿¡` inverted-mark typography detector — calibrated NOT to false-fire on clean native prose.

**Four content-types** (each with its own adapter): marketing long-form, short-comms, technical, editorial-SEO.

**Optional external integration:** live scoring via Copyleaks, GPTZero, or Originality.ai (`--external <provider>`). Lazy `httpx` import, so the analyzer works fully offline.

## What's inside

```
human-writer-es/
├── SKILL.md                          # Orchestration hub: routing + master checklist + anti-patterns (es)
├── README.md                         # This file
├── INSTALL.md                        # Installation instructions
├── requirements.txt                  # pyyaml (required) + httpx (optional)
├── references/
│   ├── tells-stylistic-es.md         # ⭐ CORE: ES suspect vocab + AI constructions + ¿¡ typography + calques
│   ├── tells-statistical.md          # burstiness / TTR (language-agnostic)
│   ├── tells-structural.md           # bullets / headers / tricolons / emoji
│   ├── humanization-techniques.md    # the ten humanization moves (Spanish worked examples)
│   ├── adapter-marketing.md          # marketing long-form adapter
│   ├── adapter-short-comms.md        # short-form comms adapter
│   ├── adapter-technical.md          # technical-docs adapter (prose-only contract)
│   ├── adapter-editorial-seo.md      # editorial-SEO adapter
│   ├── external-detectors.md         # Copyleaks / GPTZero / Originality.ai integration notes
│   └── checklists.md                 # pre-publish checklists + Spanish quick-triage
└── scripts/
    ├── rules.yaml                    # ⭐ es: vocab + constructions + thresholds (incl. inverted_marks_missing_max)
    └── analyze.py                    # ⭐ es-adapted: tricolon (y|e) + detect_inverted_marks
```

## Installation

See `INSTALL.md`. TL;DR for macOS/Linux:

```bash
mkdir -p ~/.claude/skills
unzip human-writer-es.zip -d ~/.claude/skills/
pip install --user -r ~/.claude/skills/human-writer-es/requirements.txt
```

## How to invoke

Once installed, the skill auto-activates on Spanish prose requests. Example prompts:

- "Escribe un artículo de 600 palabras sobre pricing de futuros del vino, que suene humano, no a IA"
- "Limpia este borrador de IA para bajar su puntuación de Copyleaks por debajo de 25"
- "Audita este correo en español para detectar tells de IA antes de enviarlo"
- "Humaniza este texto, suena demasiado a ChatGPT"
- "Make this Spanish landing-page copy read human, not AI"

If auto-activation misses, force it: "Use the `human-writer-es` skill to..."

## The analyzer

`scripts/analyze.py` is a deterministic scorer that runs offline. It loads `scripts/rules.yaml` (Spanish vocab lists, regex patterns, thresholds) and emits a 0-100 score plus a list of flagged tells.

```bash
# Audit mode (default, JSON output for tooling)
python3 scripts/analyze.py --input draft.md --lang es --type marketing

# Human-readable report
python3 scripts/analyze.py --input draft.md --lang es --type editorial-seo --format human

# Pipe via stdin
cat draft.md | python3 scripts/analyze.py --lang es --type technical --format human
```

Required flags: `--lang es`, `--type` (`marketing` / `short-comms` / `technical` / `editorial-seo`). `--input` is optional; stdin otherwise.

**Score bands** (4-band YAML, canonical):
- `0-24` **LOW_RISK:** ship it.
- `25-49` **MEDIUM_RISK:** apply the top 3 recommendations, re-score.
- `50-74` **HIGH_RISK:** in WRITE mode restart; in CLEAN mode apply a stronger rewrite.
- `75-100` **CRITICAL:** major rewrite.

**Detectors implemented:** em-dash density, sentence-length stdev (burstiness), TTR (lexical diversity), Spanish suspect-vocabulary, Spanish AI-construction regex bank, Spanish tricolon (`y`/`e`), bullet parallelism, header pyramid, and the Spanish-only **`¿¡` inverted-mark** detector (low-weight, register-calibrated).

**Prose-only scoring.** The analyzer strips fenced code blocks, markdown data tables, and opt-in ignore regions before scoring. Wrap any intentionally AI-flavored citation so it doesn't count against you:

```
<!-- human-writer:ignore-start (cita de mal ejemplo) -->
En el mundo actual, cabe destacar soluciones robustas sin fisuras.
<!-- human-writer:ignore-end -->
```

## What's NOT inside

- **English / French content:** use `human-writer-en` / `human-writer-fr`. Other locales: `human-writer-pt` / `-de` / `-ar` / `-hi`.
- **Document structure** (which sections, which schemas, which headings): use a dedicated structure/content tool. This skill is the stylistic filter applied on top of whatever produces the structure.
- **Technical SEO audit of a web project:** use a dedicated SEO tool. This skill handles content style only.

This skill is a stylistic filter invoked on top of structure-producing tools, never as a replacement.

## Part of the mr-bridge.com toolkit

This skill is part of the [mr-bridge.com](https://mr-bridge.com) toolkit for scraping, data, and content automation. Related resources:

- [mr-bridge.com](https://mr-bridge.com) — home
- [Scrapers](https://mr-bridge.com/scrapers) — the Apify Actor portfolio
- [MCP servers](https://mr-bridge.com/mcp-servers) — Model Context Protocol servers
- [AI workflows](https://mr-bridge.com/ai-workflows) — agents and automation
- [Studies](https://mr-bridge.com/studies) — data studies and one-pagers
- [Articles](https://mr-bridge.com/articles) — write-ups and guides
- [Solutions](https://mr-bridge.com/solutions) — end-to-end solutions

## License

Personal use. Customize freely. No warranty. The external-detector endpoints in `analyze.py` are language-agnostic POSTs and carry `# (verify)` markers; they were not re-verified for Spanish specifically.

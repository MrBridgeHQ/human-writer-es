---
name: human-writer-es
description: Use when writing, cleaning, or auditing SPANISH prose so it reads as human-authored and survives AI detectors. Triggers on "escribir como humano", "humanizar este texto", "limpiar texto de IA", "auditar riesgo de detección IA", "hacer que este texto suene menos a ChatGPT", "puntuar para Copyleaks", plus English equivalents that name Spanish ("make this Spanish text read human", "humanize this Spanish draft", "clean AI tells from Spanish copy", "audit Spanish text for AI detection"). Spanish specialization, part of the human-writer per-language family (English: human-writer-en, French: human-writer-fr). Covers es only, four content-types (marketing long-form / short-form comms / technical docs / editorial-SEO), three modes (write / clean / audit). Adds Spanish-specific doctrine: ¿¡ inverted marks, raya vs Anglo em-dash, EN→es calques (aprovechar, sin fisuras, robusto), conclusion templates (en definitiva / en última instancia). Targets sub-25% AI-probability on Copyleaks/GPTZero.
---

# Human Writer — Spanish (es)

You are an expert at producing **Spanish** prose that reads as human-authored and at sanitizing Spanish AI drafts to eliminate the statistical, stylistic, structural, and typographic tells used by commercial AI detectors.

This is the **Spanish member** of the `human-writer` per-language family — one autonomous skill per language (`en`, `fr`, `es`, `pt`, `de`, `ar`, `hi`), all built on the same architecture. It operates in **three modes** (WRITE / CLEAN / AUDIT), in **one language** (es), across **four content-types** (marketing long-form / short-form comms / technical docs / editorial-SEO).

## When to use this skill

Activate when the request involves **Spanish** content and any of:
- Writing a new piece of Spanish prose that should not pattern-match as AI output
- Rewriting an existing Spanish AI draft to remove tells
- Auditing a Spanish draft for AI-detection risk before publication

For other languages, use the matching member of the family: English → `human-writer-en`; French → `human-writer-fr`; Brazilian Portuguese → `human-writer-pt`; German → `human-writer-de`; Arabic (RTL) → `human-writer-ar`; Hindi (Devanagari) → `human-writer-hi`.

This skill is a **stylistic quality filter**: it cleans prose, it does not invent document structure.

## Routing

```
What does the user want (in Spanish)?
├── Produce new content                  → MODE: WRITE
├── Transform an existing text           → MODE: CLEAN
├── Diagnose / score without rewrite     → MODE: AUDIT
└── Unclear                              → Ask ONE question: "¿escribir, limpiar o auditar?"
```

After mode is set, identify (content-type, target length). The language is always `es`. If content-type is ambiguous, ask one question maximum.

## Load on demand

Based on routing, load:

| Trigger | Load |
|---|---|
| Any mode (always, language es) | `references/tells-stylistic-es.md` |
| Any mode | `references/tells-statistical.md`, `references/tells-structural.md` |
| WRITE or CLEAN | `references/humanization-techniques.md` |
| Adapter by content-type | `references/adapter-marketing.md` OR `adapter-short-comms.md` OR `adapter-technical.md` OR `adapter-editorial-seo.md` |
| AUDIT with `--external` requested | `references/external-detectors.md` |
| Pre-publish self-check | `references/checklists.md` (includes the Spanish quick-triage) |

## URL fetch guardrail

If the user provides a URL, fetch via a hosted scraping/search tool (e.g. `firecrawl_scrape` with `onlyMainContent: true`, Tavily, or Exa). Do NOT use `requests`/`httpx`/`puppeteer`/`curl` in custom code. The `analyze.py` script accepts a file or stdin only — it never fetches the network for the input text.

## Master checklist (all modes)

Before delivering any text:

1. Run `scripts/analyze.py --input <draft> --lang es --type Y --format human`
2. If score ≤ 24 (LOW_RISK): deliver with the report.
3. If score 25–49 (MEDIUM_RISK): apply the top 3 recommendations, re-score, deliver.
4. If score ≥ 50 (HIGH_RISK / CRITICAL): in WRITE mode, restart from a different angle; in CLEAN mode, apply a stronger rewrite strategy from `humanization-techniques.md`.

Verdict bands are the 4-band YAML scheme (canonical): LOW_RISK [0,24], MEDIUM_RISK [25,49], HIGH_RISK [50,74], CRITICAL [75,100]. A score of 24 is LOW; 25 is MEDIUM; 75+ is CRITICAL.

## What makes the Spanish side different

The Spanish-specific detectors catch what English-trained tools miss:

- **Inverted opening marks `¿` / `¡`** — Spanish opens questions with `¿` and exclamations with `¡`. AI plain-text output frequently drops them, emitting only the closing `?` / `!`. A `?`/`!`-terminated sentence missing its matching opener is a strong tell, wired as the `detect_inverted_marks` branch.
- **Anglo spaced em-dashes "—"** in expository prose (> 1 per 1000 words) — native Spanish reserves the raya for dialogue; convert the Anglo emphasis dash to comma, colon, period, or parentheses.
- **EN→es calques** — "aprovechar" (leverage), "sin fisuras" / "fluido" (seamless), "accionable" (actionable), "soportar una función" (support a feature), "librería" (library), "remover" (remove), "eventualmente" (eventually).
- **Suspect vocabulary** — "cabe destacar", "en el mundo actual", "sin lugar a dudas", "robusto", "transformador", "imprescindible".
- **AI constructions** — "No se trata solo de X, sino de Y", "Sumérgete en…", "Ya seas X o Y", "Imagina un mundo donde".
- **Conclusion clichés** — "En conclusión", "En definitiva", "En última instancia", "En resumen".

## Anti-patterns (rejected by this skill)

- Bullets where every item starts with the same verb
- Anglo spaced em-dashes "—" in expository prose (> 1 per 1000 words); keep only genuine dialogue rayas
- A `?`/`!`-terminated sentence missing its opening `¿`/`¡` (outside chat/SMS register)
- Tricolons ("X, Y y Z" / "X, Y e Z") more than once per 200 words
- Vocabulary from the suspect list (see `tells-stylistic-es.md`): "cabe destacar", "en el mundo actual", "sin lugar a dudas", "sumérgete en", "aprovechar", "sin fisuras", "robusto", "transformador"
- AI constructions: "No se trata solo de X, sino de Y", "Ya seas X o Y", "Imagina un mundo donde"
- Header pyramids (H2 → 3× H3 systematically)
- Conclusions that begin with "En conclusión", "En definitiva", "En última instancia", "En resumen"
- EN→es calques in translated copy: "sin fisuras" (seamless), "accionable" (actionable), "soportar una función" (support), "librería" (library), "remover" (remove), "eventualmente" (eventually)

## See also

Part of the `human-writer` per-language family — one autonomous skill per language, same architecture and reference set: English (`human-writer-en`), French (`human-writer-fr`), Spanish (this skill), Brazilian Portuguese (`human-writer-pt`), German (`human-writer-de`), Arabic (`human-writer-ar`), and Hindi (`human-writer-hi`).

---

Part of the **[mr-bridge.com](https://mr-bridge.com)** toolkit for scraping, data, and content automation — see [Articles](https://mr-bridge.com/articles), [Studies](https://mr-bridge.com/studies), and [AI workflows](https://mr-bridge.com/ai-workflows).

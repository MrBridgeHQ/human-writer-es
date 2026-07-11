# Human Writer - Spanish

Make Spanish AI text read as human-authored, and audit any Spanish draft with a **deterministic 0-100 AI-detection score** before you publish. A Claude Code Agent Skill.

The Spanish member of the `human-writer` per-language family (English, French, Spanish, Portuguese, German, Arabic, Hindi). Each member installs side by side and activates only on its own language triggers.

## Three modes

- **Write:** produce new Spanish content already engineered to score low-risk.
- **Clean:** rewrite an existing Spanish AI draft to strip detector tells, preserving meaning.
- **Audit:** score a Spanish draft, surface the worst tells, and recommend fixes without rewriting it.

Four content types are supported (marketing long-form, short-form comms, technical docs, editorial-SEO), each with its own tolerances.

## Why it exists

Modern LLM output is fluent enough to ship but carries fingerprints that commercial detectors (Copyleaks, GPTZero, Originality.ai) latch onto: low burstiness, repeated vocabulary, formulaic frames, and typographic tells. A draft rejected at 70 percent or more does not need a rewrite from scratch; it needs a disciplined sweep of the specific tells the detectors weight. This skill encodes that doctrine for Spanish and ships a scorer, targeting sub-25 percent AI-probability on Copyleaks and GPTZero.

## Spanish-specific doctrine

- Inverted-mark discipline (the opening question and exclamation marks) and the raya versus the Anglo em-dash (U+2014).
- EN-to-ES calques are flagged (aprovechar, sin fisuras, robusto) along with conclusion frames (en definitiva, en ultima instancia).

## The analyzer

`scripts/analyze.py` is a deterministic 0-100 scorer that runs offline (it loads `rules.yaml`; optional live scoring via Copyleaks, GPTZero, or Originality.ai with `--external`).

```bash
python3 skills/human-writer-es/scripts/analyze.py --input draft.md --lang es --type marketing --format human
```

Score bands: 0-24 low-risk (ship it), 25-49 medium (apply the top fixes and re-score), 50-74 high, 75-100 critical.

## Installation

```bash
cp -r skills/human-writer-es ~/.claude/skills/
pip install -r skills/human-writer-es/requirements.txt   # pyyaml required, httpx optional
```

Or copy `skills/human-writer-es` into a project's `.claude/skills/` directory.

## Use it

Once installed, the skill auto-activates on Spanish prose requests. Example prompts:

- "Humaniza este texto para que no parezca de IA"
- "Limpia este borrador de IA y apunta a un Copyleaks bajo 25"
- "Audita el riesgo de deteccion de IA de este articulo"

Force activation: "Use the `human-writer-es` skill to ...".

## What is inside

The skill lives in [`skills/human-writer-es/`](skills/human-writer-es/): a `SKILL.md` (routing, master checklist, anti-patterns), a `references/` library (stylistic, statistical, and structural tells, humanization techniques, and per-content-type adapters), and `scripts/` (`rules.yaml` plus the `analyze.py` 0-100 scorer and its tests).

## License

See `LICENSE`.

---

Part of the **[mr-bridge.com](https://mr-bridge.com)** toolkit for scraping, data, and content automation:
[Scrapers](https://mr-bridge.com/scrapers) · [MCP servers](https://mr-bridge.com/mcp-servers) · [AI workflows](https://mr-bridge.com/ai-workflows) · [Studies](https://mr-bridge.com/studies) · [Articles](https://mr-bridge.com/articles) · [Solutions](https://mr-bridge.com/solutions)

---

*Part of the [MrBridge Agent Skills catalog](https://github.com/MrBridgeHQ/skills). Browse them all at [mr-bridge.com/skills](https://mr-bridge.com/skills).*

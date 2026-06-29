# Pre-Publish Checklists (human-writer-es)

> Ready-to-paste self-review checklists, one per content-type, for Spanish prose. Run `analyze.py --lang es` first, then walk through the relevant checklist before delivery. Each checklist is short, actionable, and covers the tells most likely to trigger AI detectors for that specific format. The Spanish quick-triage at the end is the Spanish-specific addition.

---

## Marketing Long-Form

Before publishing blogs, READMEs, landing pages, or long-form newsletters in Spanish, confirm:

- [ ] Analyzer score ≤ 24 with `--lang es --type marketing`
- [ ] First 100 words contain zero Tier-1 suspect vocabulary
<!-- human-writer:ignore-start (checklist quotes the tells to look for) -->
- [ ] First paragraph does not open with "En el mundo actual", "En la era digital", "Cabe destacar", or "Ya seas X o Y"
- [ ] Closing paragraph does not start with "En conclusión", "En definitiva", "En última instancia", or "En resumen"
<!-- human-writer:ignore-end -->
- [ ] Em-dash count ≤ 1 per 1000 words (run `analyze.py` to check); only genuine dialogue rayas allowed
- [ ] Every `?`/`!` has its matching opening `¿`/`¡`
- [ ] At least one specific number, named entity, or first-person opinion per ~300 words
- [ ] Bulleted lists vary opening verbs (≤ 80% share the same first word)
- [ ] No H2 has exactly 3 H3 children (if 2+ H2s exist, vary H3 counts)
<!-- human-writer:ignore-start (checklist quotes the tells to look for) -->
- [ ] No "Puntos clave" / "Lo que aprenderás" / "Las X mejores" standalone block
<!-- human-writer:ignore-end -->
- [ ] No emoji as section header

If any item fails: fix before delivery. If analyzer score is 25–49 after fixes, apply the top 3 recommendations and re-score. If 50+, reconsider your angle.

---

## Short-Form Communications

Before sending emails, LinkedIn posts, or customer replies in Spanish, confirm:

- [ ] Analyzer score ≤ 24 with `--lang es --type short-comms`
<!-- human-writer:ignore-start (checklist quotes the tells to look for) -->
- [ ] No "Espero que este mensaje te encuentre bien" opening
- [ ] No "Quedo a la espera de tu respuesta" / "Sin otro particular" closing
- [ ] No "Me pongo en contacto contigo para", "No dudes en escribirme", "Para cualquier duda, no dudes en"
<!-- human-writer:ignore-end -->
- [ ] Em-dashes: 0 preferred, never 2+ in messages under 200 words
- [ ] At least one contraction, sentence fragment, or first-person verb in replies over 30 words
- [ ] Signoff is first name, short phrase, or nothing, not corporate boilerplate ("Un cordial saludo" every email)
<!-- human-writer:ignore-end -->
- [ ] First line is not "Me dirijo a ti" / "Te escribo para" / "Quería ponerme en contacto"

If any item fails: revise before sending. (Note: in casual chat/SMS register, dropping `¿`/`¡` is acceptable; the analyzer's `inverted_marks_missing_max` is looser under `--type short-comms`.)

---

## Technical Documentation

Before publishing internal READMEs, RFCs, or technical journals in Spanish, confirm:

- [ ] Analyzer score ≤ 24 with `--lang es --type technical`
<!-- human-writer:ignore-start (checklist quotes the tells to look for) -->
- [ ] First sentence states the WHY (problem this doc solves), not "En este documento, vamos a explorar..."
- [ ] No "¡Vamos al lío!" / "¡Empecemos!" / "Sin más preámbulos" filler
- [ ] No "Conclusión" section (unless >500 words and earns a summary)
- [ ] Every instance of "robusto", "escalable", "aprovechar", "elegante", "potente" passes the "replace with 'bueno'" test
<!-- human-writer:ignore-end -->
- [ ] Code blocks are not surrounded by paragraphs that re-explain them line-by-line
- [ ] One sentence per concept: no restating or hedging the same idea twice
<!-- human-writer:ignore-start (checklist quotes the tells to look for) -->
- [ ] Zero hedging openers ("Cabe destacar", "Conviene recordar", "Es importante tener en cuenta", "Nota:")
<!-- human-writer:ignore-end -->

If any item fails: revise. Technical docs should be direct and economical.

---

## Editorial-SEO Articles

Before publishing ranking-optimized articles in Spanish, confirm:

- [ ] Analyzer score ≤ 24 with `--lang es --type editorial-seo`
- [ ] Target keyword appears in: title, first 100 words, and ≥1 H2
- [ ] First 100 words contain a specific data point or opinion (not just the keyword)
- [ ] H2 hierarchy is varied, not pyramid (not 3 H3s per H2 uniformly)
- [ ] At least 1 internal link with natural anchor text (not "haz clic aquí")
<!-- human-writer:ignore-start (checklist quotes the tells to look for) -->
- [ ] No "En el mundo actual de X," / "En la era digital," opener
- [ ] No "Conclusión" that just restates the intro / tl;dr
<!-- human-writer:ignore-end -->
- [ ] At least one opinion that someone could reasonably disagree with
<!-- human-writer:ignore-start (checklist quotes the tells to look for) -->
- [ ] No "Guía definitiva", "Todo lo que necesitas saber", "Guía completa" UNLESS your keyword data demands it
<!-- human-writer:ignore-end -->
- [ ] Sentence-length standard deviation ≥ 8 (mix short and long)
- [ ] Title in sentence case, not Title Case Every Word

If any item fails: fix before publishing.

---

## Universal Baseline

Apply to **all** content types before delivery:

- [ ] Final `analyze.py --lang es` run; score ≤ 24
- [ ] No Tier-1 suspect vocabulary in the first 100 words (check `rules.yaml` for the list)
- [ ] Every `?`/`!` carries its opening `¿`/`¡` (except deliberate chat/SMS register)
- [ ] At least one specific element: number, name, date, fact, quote, not generic claims
- [ ] At least one stylistic asymmetry: a short sentence after long ones, a varied list length, unexpected structure
- [ ] Doesn't end with a summary or call-to-action that merely restates the opening

---

## Spanish quick-triage (Spanish-specific)

A 60-second eyeball pass for any Spanish draft, in priority order — the fastest path from "looks AI" to "reads human". Mirrors the order in `tells-stylistic-es.md` § Quick triage:

1. **Inverted marks.** Scan every `?` and `!`. Missing `¿`/`¡`? Add it. (One omission flags; several is a strong tell.)
2. **Spaced em-dashes.** Count Anglo "—" in expository prose. >1 per 500 words → replace with comma/colon/period/parentheses. Genuine dialogue rayas don't count.
3. **Opener.** First sentence starts with "en el mundo actual / en la era digital / cabe destacar / sumérgete en"? Rewrite.
4. **Closer.** Last paragraph starts with "en definitiva / en última instancia / en conclusión / en resumen"? Rewrite.
5. **Tier-1 vocab.** "aprovechar (leverage), sin fisuras, robusto, potenciar, empoderar, transformador, imprescindible" — cap 1 per paragraph.
6. **Constructions.** "no se trata solo de…, sino de…", "ya seas… o…", "sin lugar a dudas".
7. **Tricolons.** Count "X, Y y Z" (and "X, Y e Z"); cap 1 per 200 words.
8. **Calques.** "sin fisuras" (seamless), "accionable" (actionable), "soportar una función" (support), "librería" (library), "remover" (remove), "eventualmente" (eventually), "asumir que" (assume).
9. **POV.** At least one first-person mark if it's opinion.
10. **Typography.** Sentence-case title, accented capitals + ñ intact, angle quotes (locale), decimal comma in es-ES.

A passing piece: 0 tier-1, ≤2 tier-2, 0 constructions, ≤1 tricolon/200w, every `?`/`!` paired, ≤1 spaced em-dash/500w, one first-person mark if opinion, title in sentence case. That lands LOW_RISK (≤ 24) and survives Copyleaks/GPTZero at sub-25 % in most domains.

---

## How to Use These Checklists

1. Write or clean your draft.
2. Run `python3 scripts/analyze.py --input <draft> --lang es --type <type> --format human` from the skill root.
3. If score > 24, apply the analyzer's top recommendations until ≤ 24.
4. Walk through the relevant checklist above (marketing, short-form, technical, or editorial-SEO) plus the Spanish quick-triage.
5. Check off each item; revise any failures.
6. Re-run the analyzer if you made major changes.
7. Deliver only when both gates pass (analyzer ≤ 24 AND checklist complete).

---

## See Also

- `tells-stylistic-es.md`: vocabulary, constructions, calques, punctuation tells (Spanish)
- `adapter-marketing.md`: doctrine specific to long-form marketing
- `adapter-short-comms.md`: doctrine specific to short communications
- `humanization-techniques.md`: positive techniques for adding human voice (Spanish examples)
- `scripts/analyze.py`: deterministic analyzer (run before checklist)
- `external-detectors.md`: optional integration with Copyleaks, GPTZero, etc.

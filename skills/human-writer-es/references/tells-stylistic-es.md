# Stylistic Tells — Spanish

> Doctrine for the `human-writer-es` skill, Spanish side. Same axes as the sibling family members (`tells-stylistic-en.md` / `tells-stylistic-fr.md`), specialized to Spanish. Doctrine is written in English; the Spanish words, phrases, and examples are the surface the analyzer matches against.

Spanish ChatGPT output, like French, runs *louder* than its English counterpart, for two reasons:

1. The model leans on a neutral-formal "español de manual" register learned from journalism (*El País*, *La Vanguardia*), academic prose, and corporate copy. That register is naturally inflated — "cabe destacar", "sin lugar a dudas", "en la era digital" — and it reads as marketing boilerplate the moment it lands on anything concrete.
2. English formulas leak through as calques: `leverage` → "aprovechar", `seamless` → "fluido / sin fisuras", `robust` → "robusto", `dive into` → "sumérgete en". A native ear catches these immediately; the model never does.

This file codifies which words, phrases, openers, closers, and typographic choices are tells in Spanish, with severity and rewrite. Spanish has one structural feature no Latin sibling shares: the **inverted opening marks `¿` and `¡`**. AI plain-text output frequently drops them. That omission is both a typographic tell and a wired detector (`detect_inverted_marks`).

---

## Suspect vocabulary (ES)

The list is calibrated against typical ChatGPT/Gemini Spanish output across marketing, editorial, and corporate copy.

**Hard rule.** Never use 2+ tier-1 items in the same paragraph. Cap any single tier-1 item at 1 per 500 words. Treat tier-1 items the way you would treat "delve" or "tapestry" in English: even one is suspicious; two is a giveaway.

**Soft rule.** Tier-2 items are legitimate in their domain. Track frequency: 3+ tier-2 items in a 300-word paragraph = the paragraph reads as AI-generated. Cap any single tier-2 item at 2 per 500 words.

**Pure-frequency rule.** Tier-3 items are individually invisible but flag the prose when 5+ co-occur in a single paragraph. The analyzer does NOT list tier-3 (false-positive risk on common Spanish words is too high for a per-word matcher); the human reviewer does.

### Tier 1 — High signal (always avoid)

These are the Spanish equivalents of English `delve`, `tapestry`, `realm`. Each line: the phrase, why it's a tell, a human alternative.

#### Connectors and meta-comments

- **"cabe destacar"** / **"cabe señalar"** / **"cabe mencionar"** / **"cabe resaltar"** — Why: meta-textual hedge; reads as report-writing. The single most frequent ES AI topic-sentence opener of 2025-2026. Alternative: drop the prefix, state the claim. "Cabe destacar que las ventas subieron" → "Las ventas subieron un 12 %."
- **"es importante destacar que"** / **"es importante señalar que"** / **"es importante mencionar que"** — Same family, English-calque flavor ("it's important to note"). Alternative: state the fact inline.
- **"es importante tener en cuenta que"** — Calque of "keep in mind that". Alternative: put the qualifier in parentheses, or drop.
- **"conviene recordar que"** / **"conviene señalar que"** / **"conviene precisar que"** — Pedantic, schoolbook. Alternative: state the fact without the meta-frame.
- **"hay que destacar"** / **"hay que señalar"** / **"hay que tener en cuenta"** — Same. Alternative: drop.
- **"sin lugar a dudas"** — Why: heavy "without a doubt" assertion AI sprinkles on any claim. Alternative: drop, or back the claim with a number.
- **"no cabe duda de que"** / **"no hay duda de que"** — Same family. Alternative: drop.
- **"como bien sabemos"** / **"como todos sabemos"** / **"como es bien sabido"** — Why: appeal to phantom consensus no native writer uses unless ironically. Alternative: drop.
- **"en este sentido"** / **"en este contexto"** — Why: meta-textual signpost AI uses to glue paragraphs. Alternative: drop; the next sentence carries the logic.
- **"a este respecto"** / **"al respecto"** (as a paragraph connector) — Same. Drop or "sobre esto".
- **"dicho esto"** (as a paragraph opener) — Fine mid-sentence; templated as an opener. Alternative: just write the next sentence.
- **"por otro lado"** / **"por otra parte"** (overused as connectors) — Schoolbook. Alternative: "y", "además", restructure.

#### Adverbs and phrases of certainty

- **"indudablemente"** / **"innegablemente"** / **"incuestionablemente"** — Why: heavy "of course" adverbs AI uses to assert authority. Alternative: drop, or "claramente".
- **"sin duda alguna"** — Cf. "sin lugar a dudas". Drop.
- **"evidentemente"** / **"obviamente"** (as openers) — Why: AI's "obviously" reflex. Alternative: drop; if it's obvious, don't say it.
- **"ciertamente"** / **"verdaderamente"** (as intensifiers) — Alternative: drop or change the adjective.

#### Spatial-temporal abstractions

- **"en el mundo actual"** / **"en el mundo de hoy"** — Why: meta-frame opener with no date, event, or actor. Alternative: name the year, the event. "En el mundo actual de los datos" → "Desde el RGPD de 2018…"
- **"en la era digital"** / **"en la era de la IA"** / **"en la era de la información"** — Same family. Alternative: a date, a fact.
- **"en la actualidad"** / **"hoy en día"** (as scene-setters) — Why: vague time-stamps. Acceptable rarely; AI overuses. Alternative: a concrete date.
- **"en un mundo donde"** / **"en una época donde"** — Why: lyrical opener. Alternative: name the actual situation.
- **"en pleno siglo XXI"** — Why: editorial cliché. Alternative: drop.
- **"a lo largo y ancho de"** — Why: lyrical "all across" cliché. Alternative: name the regions, or "por todo".
- **"en el corazón de"** (when not literal anatomy/geography) — Calque of "at the heart of". Alternative: "en el centro de", "dentro de", or drop.
- **"en el seno de"** — Calque of "within / au sein de". AI uses it for any "in" inside a noun phrase. Alternative: "dentro de", "en".
- **"más allá de"** (overused metaphorical scope-broadener) — Alternative: "además de", "aparte de".

#### Comparators and frames

- **"a la luz de"** — Calque of "in the light of". Alternative: "a partir de", "teniendo en cuenta", "visto".
- **"en aras de"** — Why: pompous "for the sake of". Alternative: "para", "con el fin de" (sparingly).
- **"de cara a"** (overused) — Alternative: "para", "pensando en".
- **"a la hora de"** (as filler before an infinitive) — Why: AI's go-to padding ("a la hora de elegir" = "when choosing"). Alternative: "al elegir", "cuando eliges".

#### Metaphorical inflators

- **"verdadero"** / **"auténtico"** (as intensifiers, e.g. "una verdadera revolución") — Why: AI's go-to amplifier for nouns. Alternative: drop or use a concrete number.
- **"todo un"** (as intensifier: "todo un referente") — Same. Alternative: name what makes it notable.
- **"imprescindible"** / **"indispensable"** (marketing usage) — Why: marketing cliché now associated with AI prose. Alternative: "necesario" (sparingly), or name the reason.
- **"referente"** (as "el referente del sector") — Marketing inflator. Alternative: "el más usado", a specific reason.
- **"emblemático"** / **"icónico"** — Why: marketing inflators. Alternative: name what makes it notable.
- **"revolucionario"** (outside literal politics) — Calque of "revolutionary". Alternative: "nuevo", "que cambia las reglas" (sparingly).
- **"transformador"** / **"transformadora"** — Calque of "transformative", barely idiomatic. Alternative: "decisivo", "importante".
- **"robusto"** / **"robusta"** (non-technical) — Calque of "robust". Alternative: "sólido", "fiable", "que aguanta".
- **"de vanguardia"** / **"puntero"** / **"de última generación"** — Calque of "cutting-edge / state-of-the-art". Alternative: "nuevo", "actual" (with a date).
- **"de primer nivel"** / **"de clase mundial"** — Calque of "world-class / best-in-class". Alternative: cite a benchmark or a number.

#### Structural metaphors

- **"la piedra angular"** / **"el pilar fundamental"** / **"la columna vertebral"** / **"el eje central"** / **"la base sobre la que"** — Why: AI scatters heroic nouns as if every concept needs one. Alternative: name the function ("X depende de Y").
- **"el motor de"** (metaphorical) — Same. Alternative: name what X actually does to Y.

#### Verbs and verbal phrases

- **"aprovechar"** (when it means "leverage", e.g. "aprovechar el potencial de") — Calque of "leverage". Alternative: "usar", "servirse de", "sacar partido de" (sparingly).
- **"aprovechar al máximo"** — Tier-1 because of the intensifier. Alternative: "usar".
- **"potenciar"** (metaphorical: "potenciar tu negocio") — Why: AI's "empower / boost" reflex. Alternative: "mejorar", "reforzar".
- **"impulsar"** (overused: "impulsar el crecimiento") — Alternative: "acelerar", "hacer crecer".
- **"empoderar"** — Calque of "empower". Outside genuine social/HR contexts, empty. Alternative: "dar los medios para", "permitir".
- **"desplegar"** (metaphorical: "desplegar una estrategia") — Why: militaristic AI cliché. Alternative: "lanzar", "poner en marcha".
- **"forjar"** / **"erigir"** / **"instaurar"** — Why: heavy verbs where "crear", "montar", "establecer" would do. Alternative: the simple verbs.
- **"encarnar"** — Why: AI's "embodies" reflex. Alternative: "representa", "es".
- **"plasmar"** / **"cristalizar"** — Same. Alternative: "resume", "refleja".
- **"catalizar"** — Same. Alternative: "desencadena", "acelera".
- **"abrazar"** (metaphorical: "abrazar el cambio") — Calque of "embrace". Alternative: "aceptar", "adoptar".
- **"sumérgete en"** / **"adéntrate en"** / **"sumergirse en"** — Why: AI's "dive into / immerse" opener. Banned as an introduction. Alternative: state the subject directly.
- **"libera el potencial de"** / **"desbloquea"** — Calque of "unlock the potential". Alternative: "usa", "aprovecha" (sparingly).

### Tier 2 — Medium signal (contextual)

Legitimate in domain (e.g. "optimizar" in an SRE post is fine). Flag when 3+ co-occur in 300 words.

#### Verbs

- **"explorar"** (metaphorical: "exploremos juntos") — Alt: "mirar", "ver", "examinar".
- **"descubrir"** (metaphorical) — Alt: "encontrar", "ver".
- **"desvelar"** / **"revelar"** — Why: marketing reveal verbs. Alt: "mostrar", "presentar".
- **"transformar"** (overused: "transforma tu negocio") — Alt: "cambiar", "mejorar".
- **"revolucionar"** — Cf. tier-1 "revolucionario". Alt: "cambiar".
- **"optimizar"** / **"agilizar"** / **"simplificar"** — Domain-fine, AI filler otherwise. Alt: name the concrete change.
- **"fomentar"** / **"favorecer"** / **"propiciar"** — Hedge-y "helps to" verbs. Alt: "facilita", verb of the actual mechanism.
- **"garantizar"** (overused) — Alt: "asegura", or state the condition.
- **"maximizar"** / **"minimizar"** — Corporate filler. Alt: "subir", "bajar", "reducir".
- **"acompañar"** (B2B "we accompany you") — Alt: "ayudar a" + verb.
- **"abordar"** (in the sense of "to address an issue") — Sometimes calque-flavored. Alt: "tratar", "resolver", "ocuparse de".
- **"gestionar"** (overused as catch-all) — Alt: name the action.
- **"implementar"** — Calque-tinged in non-technical copy. Alt: "poner en marcha", "aplicar".
- **"monitorear"** / **"monitorizar"** — Alt: "vigilar", "seguir".

#### Adjectives of importance / intensity

- **"clave"** / **"fundamental"** / **"esencial"** / **"crucial"** / **"primordial"** / **"vital"** — All inflators. AI sprays them. Alt: drop, or quantify.
- **"destacado"** / **"notable"** / **"relevante"** / **"significativo"** — Empty modifiers. Alt: the number.
- **"extraordinario"** / **"excepcional"** / **"impresionante"** / **"asombroso"** / **"espectacular"** — AI's intensifier toolkit. Alt: name the specific quality.
- **"único"** (as "una experiencia única") — Alt: name what's actually different.
- **"innovador"** / **"innovadora"** — Empty self-praise. Alt: "nuevo", and show why.
- **"poderoso"** / **"potente"** (marketing) — Alt: a benchmark or number.
- **"elegante"** / **"sofisticado"** / **"intuitivo"** — Product-copy cliché. Alt: name the design choice.

#### Abstract nouns

- **"sinergia"** / **"sinergias"** — Buzzword. Alt: name the relationship.
- **"ecosistema"** (metaphorical, outside biology) — Calque of "ecosystem". Alt: "mercado", "red", "comunidad".
- **"universo"** (metaphorical: "el universo del vino") — Alt: "el mundo del vino", "el sector del vino", or drop.
- **"mundo de"** (metaphorical: "el mundo digital") — Alt: "el sector digital", "la tecnología".
- **"paradigma"** — Academic filler outside Kuhn. Alt: "modelo", "enfoque".
- **"experiencia"** (vague usage: "una experiencia inolvidable") — Alt: name what the user actually does.
- **"solución"** (vague, "nuestra solución") — Alt: the actual thing: "el panel", "el cron", "la exportación CSV".
- **"viaje"** / **"trayecto"** / **"recorrido"** (metaphorical) — Tourism/UX cliché. Alt: name the steps.
- **"abanico"** ("un amplio abanico de") — Alt: a number, "varios".
- **"sinfín"** ("un sinfín de posibilidades") — Alt: a number, drop.
- **"multitud de"** / **"una gran variedad de"** — Alt: "muchos", a number.

#### Connectors (overuse)

- **"además"** / **"asimismo"** / **"igualmente"** — Schoolbook. Alt: "y", "también".
- **"por consiguiente"** / **"por ende"** / **"por lo tanto"** (heavy) — Alt: "así que", "entonces".
- **"no obstante"** / **"sin embargo"** (every paragraph) — Alt: "pero", restructure.
- **"de hecho"** (as filler) — Alt: drop.

### Tier 3 — Low signal (frequency-only)

Individually fine. Flag a paragraph if 5+ co-occur. (The analyzer does not list these; the reviewer does.)

enfoque, planteamiento, estrategia, reto, desafío, oportunidad, perspectiva, visión, ambición, rendimiento, eficiencia, rentabilidad, crecimiento, acompañamiento, valor añadido, beneficio, ventaja, fortaleza, recurso, potencial, dinámica, palanca, eje, pilar, dimensión, faceta, aspecto, elemento, componente, ámbito, marco, gobernanza, alineación, coherencia, transversalidad, transparencia, fluidez, sencillez, eficacia, robustez, escalabilidad, modularidad, interoperabilidad, sostenibilidad, RSC, impacto, trazabilidad, monitorización, observabilidad, automatización, industrialización.

**Why low signal**: each appears naturally in honest Spanish B2B prose. **Why they still matter**: a paragraph with 5+ of them is corporate AI Esperanto.

### Replacements (consolidated)

| Tell | Human alternative |
|---|---|
| cabe destacar / cabe señalar | drop and state the claim |
| es importante destacar que | drop; state the fact inline |
| es importante tener en cuenta que | parenthesize the qualifier, or drop |
| sin lugar a dudas / no cabe duda | drop, or back with a number |
| en el mundo actual | hoy / desde [fecha] / aquí |
| en la era digital | hoy / desde [fecha concreta] |
| sumérgete en / adéntrate en | mira / examina / aquí está |
| exploremos / descubre | veamos / mira / aquí |
| libera el potencial de | usa / aprovecha (sparingly) |
| robusto (no técnico) | sólido / fiable / que aguanta |
| transformador | importante / decisivo / que cambia las reglas |
| en el corazón de | en el centro de / dentro de |
| en el seno de | dentro de / en |
| imprescindible (marketing) | necesario (con moderación) / name the reason |
| una multitud de / un sinfín de | muchos / varios / decenas de (concrete) |
| un amplio abanico de | una decena de / varios / Ø |
| aprovechar (leverage) | usar / servirse de / sacar partido de (sparingly) |
| aprovechar al máximo | usar |
| potenciar / impulsar | mejorar / acelerar / hacer crecer |
| empoderar | dar los medios para / permitir |
| desplegar (estrategia) | lanzar / poner en marcha |
| forjar / erigir / instaurar | crear / montar / establecer |
| encarnar | representa / es |
| catalizar | desencadena / acelera |
| abrazar (el cambio) | aceptar / adoptar |
| piedra angular / pilar fundamental / columna vertebral | name the function literally |
| ecosistema (metaphorical) | mercado / red / comunidad |
| universo del X | sector X / el mundo del X / el X |
| de vanguardia / de última generación | nuevo / actual (with a date) |
| de clase mundial | cite a benchmark or number |
| además / asimismo | y / también |
| por consiguiente / por ende | así que / entonces |

---

## AI constructions (ES)

Patterns the analyzer matches via regex. Severity drives scoring.

### High severity

#### "No se trata solo de X, sino de Y"

Calque of "It's not just X, it's Y". Never use. Replace with a concrete claim.

- Evitar: "No se trata solo de una herramienta de pricing, sino de un activo estratégico."
- Preferir: "La herramienta expone los márgenes por referencia — los mismos números que miran los compradores."

#### "Sumérgete en…" / "Adéntrate en…" / "Exploremos juntos…"

Never use as an introduction. State the subject directly.

- Evitar: "Sumérgete en el fascinante mundo del pricing dinámico."
- Preferir: "Pricing dinámico — empecemos por los umbrales de margen."

#### "En el mundo actual…" / "En la era digital…" / "En la era de la IA…"

Never open with a temporal abstraction. Use a date, an event, or jump straight in.

- Evitar: "En el mundo actual, donde los datos son el nuevo petróleo…"
- Preferir: "Desde el RGPD, exportar tu base de clientes cuesta más."

#### "Imagina un mundo donde…" / "¿Y si te dijera que…?"

Conference-bro openers. Banned. (Note: the second already carries `¿`; the tell is the rhetorical frame, not the punctuation.)

- Evitar: "Imagina un mundo donde tus clientes pagan antes de comprar."
- Preferir: "El prepago ya existe — Wine.com lo hace desde 2003."

#### "Sin lugar a dudas…" / "No cabe duda de que…"

Cf. suspect vocab. Pattern-matched separately because it acts as a topic-sentence opener.

- Evitar: "Sin lugar a dudas, los márgenes están cayendo."
- Preferir: "Los márgenes caen. Cuatro puntos en dos años."

#### "Cabe destacar que…" / "Cabe señalar que…"

The strongest single-phrase ES topic-sentence tell of 2025-2026. Pattern-matched because it fronts a claim.

- Evitar: "Cabe destacar que la migración mejoró el rendimiento."
- Preferir: "La migración bajó la latencia un 40 %."

### Medium severity

#### "Ya seas X o Y" / "Tanto si eres X como si eres Y"

Avoid unless the branching is real. By default, pick one reader and write for them.

- Banido por defecto: "Ya seas una startup o una gran empresa…"
- Aceptable si real: "Tanto si facturas en EUR como en USD, la exportación es idéntica."

#### "Prepárate, porque…" / "Agárrate, que…"

AI signal-flares to the reader. Cut them; the sentence after is the actual content.

#### "Vamos a desglosarlo." / "Déjame explicártelo." / "Vamos al grano."

Meta-sentences that perform thinking instead of doing it. Skip to the decomposition.

#### "En pocas palabras," / "Para resumir," / "En resumidas cuentas,"

Closers that announce a summary. Either summarize, or don't — don't announce.

#### "Quizás te preguntes…" / "Tal vez te estés preguntando…"

AI's "you might be wondering" reflex. Bad. Just answer the implied question.

#### "¿El resultado? X." / "¿La conclusión? X." / "¿Por qué importa? Porque…"

Question-then-answer pattern AI overuses. Native Spanish does it occasionally; AI does it every paragraph. Cap at 1 per 800 words.

#### "El veredicto es claro:" / "La conclusión es evidente:"

AI's "the verdict is clear" reflex. Drop.

### Low / conclusion severity

#### Conclusion openers: "En definitiva," / "En resumen," / "En última instancia," / "En conclusión," / "Para concluir," / "En síntesis,"

Conclusion templates. **"En definitiva" and "en última instancia" are the strongest ES closing tells** (the latter a direct calque of "ultimately"). Cap all at 0 as paragraph openers.

#### "Dicho esto," / "Ahora bien," (as paragraph openers)

Pseudo-hedges. Each acceptable rarely; AI overuses. Cap at 1 per 800 words.

### Hedging openers (drop entirely)

- "Es importante destacar que"
- "Es importante señalar que"
- "Conviene recordar que"
- "Hay que tener en cuenta que"
- "Cabe mencionar que"

If the qualifier matters, state it inline. Example: "El pricing depende del volumen (importante: sin IVA)."

---

## Em-dash and raya discipline

**Ban the em-dash "—" (U+2014) used as an Anglo-style parenthetical/rhetorical dash. Target 0; hard cap ≤ 1 per 1000 words.** As in French, in Spanish the wide "—" used like English (spaced, mid-sentence, for emphasis) reads as machine output on sight, because that usage is an AI signature, not native Spanish typography. Convert every such "—" to a comma, colon, period, or parentheses.

Spanish *does* have a legitimate native use of the raya (`—`): **dialogue and incises within dialogue**, and a paired raya for parenthetical insertion in literary prose. The tell is not the character itself but the AI pattern: spaced Anglo dashes sprayed through expository/marketing prose. When cleaning or writing ES, sweep for "—" explicitly and remove every occurrence that is not genuine dialogue.

### Why ES (like FR) is stricter than EN

- Native Spanish expository prose prefers commas for short asides, colons for setups, parentheses for true asides, and periods for emphatic separation.
- The incise (la herramienta, diseñada para X, funciona a diario) uses commas, not dashes, by default.
- The raya in Spanish belongs to **diálogo** (—Hola —dijo—) and to paired parenthetical insertion in literary text. AI conflates this with the English emphasis-dash and over-applies it.
- The RAE convention is that the raya in incises is written **without spaces against the inserted text** (—como esta—), whereas AI tends to emit spaced Anglo dashes ( — like this — ). The spacing pattern itself is a tell.

### When the raya IS appropriate in ES

1. **Diálogo.** "—Ya voy —dijo." opens a speaker line and marks the dialogue tag.
2. **Paired parenthetical incise** where parentheses would feel too weak and commas ambiguous (because the clause already contains commas). Rare in expository prose. Written tight: "El coste —nada despreciable— sigue siendo competitivo."

### Replacement table

| AI overuse | Human ES |
|---|---|
| "Rápido — eficaz — simple." | "Rápido, eficaz, simple." or "Rápido. Eficaz. Simple." |
| "La herramienta — diseñada para bodegas — funciona a diario." | "La herramienta, diseñada para bodegas, funciona a diario." |
| "Funciona — la mayoría de las veces." | "Funciona (la mayoría de las veces)." |
| "Es simple — y funciona." | "Es simple. Y funciona." |
| "Tres opciones — A, B y C — todas válidas." | "Tres opciones: A, B y C. Todas válidas." |
| "El coste — no despreciable — sigue siendo competitivo." | "El coste, no despreciable, sigue siendo competitivo." |
| "Pricing flexible — pago por evento." | "Pricing flexible: pago por evento." |

---

## Calques anglosajones a evitar (anglicismos IA)

These English-origin patterns leak into Spanish ChatGPT output. They're stronger tells in Spanish than in English because they read as unnatural to a native ear.

### Lexical calques

- **"aprovechar"** (leverage, when overused as the default "use") → "usar", "servirse de", "sacar partido de"
- **"sin fisuras"** / **"fluido"** (seamless) → "sin problemas", "directo", "sin pegamento de por medio". "Sin fisuras" in particular is the canonical ES rendering of "seamless" and a heavy tell.
- **"robusto"** (non-technical, robust) → "sólido", "fiable"
- **"transformador"** (transformative) → "decisivo", "importante"
- **"escalable"** (scalable, in marketing) → state the capacity number
- **"accionable"** (actionable) → "aplicable", "que se puede aplicar". "Accionable" in Spanish properly means *operable by a mechanism* (a button, a lever); the "actionable insight" sense is a calque.
- **"impactar"** (to impact, transitively) → "afectar a", "influir en". In careful Spanish "impactar" is intransitive-ish ("impactar en"); AI drops the preposition.
- **"customizar"** (customize) → "personalizar"
- **"setear"** / **"resetear"** (set / reset) → "configurar", "reiniciar"
- **"aplicar a un puesto"** (apply to a job, calque) → "presentarse a", "solicitar"
- **"asumir que"** (assume that) → "suponer que", "dar por hecho que". "Asumir" in Spanish = take on responsibility, not "suppose".
- **"realizar"** (overused for "do/make", calque of "realize a task") → "hacer", "llevar a cabo" (sparingly)
- **"en orden de"** (in order to, calque) → "para", "con el fin de"
- **"basado en"** (based on, before main verb where "según" fits) → "según", "a partir de"
- **"remover"** (remove, calque — in Spain "remover" = stir) → "quitar", "eliminar"
- **"librería"** (library, software calque) → "biblioteca" (for a code library)
- **"eventualmente"** (eventually, calque — ES "eventualmente" = occasionally) → "con el tiempo", "al final"

### Calques de traducción (EN→ES)

When **translating** EN source into ES (not writing fresh), a second class of calque appears: domain terms rendered word-for-word into ES strings that either don't exist or mean something else. They pass every "fluency" check yet read as machine output to a native professional.

| EN source | Calque (avoid) | Idiomatic ES | Note |
|---|---|---|---|
| seamless integration | "integración sin fisuras" | **"integración directa" / "se integra sin líos"** | "sin fisuras" is the AI fingerprint for "seamless" |
| actionable insights | "información accionable" | **"información aplicable" / "datos que puedes usar"** | "accionable" = operable by a mechanism, not "actionable" |
| default (value) | "el default" | **"el valor por defecto" / "el valor predeterminado"** | |
| to support a feature | "soportar una función" | **"admitir / permitir / ser compatible con"** | "soportar" = to endure/bear, not "to support a feature" |
| library (software) | "librería" | **"biblioteca"** | "librería" = bookshop |
| to remove | "remover" | **"quitar" / "eliminar"** | "remover" = to stir (Spain) |
| eventually | "eventualmente" | **"con el tiempo" / "al final"** | "eventualmente" = occasionally in ES |
| relatable | "relacionable" | name the real thing: **"con lo que te identificas"** | no clean ES word; don't transliterate |
| world-class | "de clase mundial" | **"de primer nivel" / "puntero"** (with restraint) | acceptable but AI-overused |
| smart money / sweet spot | "smart money" / "sweet spot" | **"dinero inteligente" / "punto óptimo"** | translate; don't leave English in body copy |

**Doctrine.** These are context-dependent (a few, like "de clase mundial", are tolerable), so they need a native judgment call, not a blind find-replace. In translated marketing/editorial copy aimed at a Spanish professional audience, prefer the idiomatic column. The tell is strongest when the calque is the **central concept** of the piece.

### Syntactic calques

- **"el más X de todos"** vs Anglo "the most X ever" → just "el más X"
- **"X-amigable"** (X-friendly) → "fácil de X", "adaptado a X" (NEVER "X-amigable")
- **"impulsado por X"** (X-driven / powered by X) → "basado en X", "con X" — fine sparingly, AI overuses
- **"listo para X"** (X-ready) → "compatible con X", "preparado para X"
- **Gerund-as-title** ("Optimizando tu flujo") — English progressive-title calque. ES prefers an infinitive or noun: "Cómo optimizar tu flujo", "Optimización del flujo".
- **Passive "es X-ado" overuse** — AI overuses the passive ("es recomendado que") where ES prefers the impersonal "se recomienda" or active voice.

### Punctuation / typography calques

- **Title Case in ES titles** (capitalizing Every Word, e.g. "Cómo Elegir Tu Vino") — wrong in ES. Spanish capitalizes only the first word and proper nouns: "Cómo elegir tu vino".
- **Missing opening `¿` / `¡`** — the single most diagnostic ES typography tell. See below.
- **Straight quotes `"X"`** instead of Spanish angle quotes `«X»` (or, in much of Latin America, curly `"X"`) — typographic tell when the rest of the document is otherwise native.
- **Oxford comma before "y"** ("A, B, y C") — Anglo. ES convention: "A, B y C" (no comma before "y").
- **Decimal point instead of comma** ("3.5 millones" where ES uses "3,5 millones") — locale tell in es-ES (Latin America varies).

---

## Spanish typography tells (the `¿¡` detector + more)

### Inverted opening marks `¿` and `¡` — the signature ES tell

Spanish is one of the few languages that opens questions with `¿` and exclamations with `¡`. **Native Spanish always uses them; AI plain-text output frequently drops them**, emitting only the closing `?` / `!` (English habit). A sentence that ends in `?` or `!` but lacks the matching opener is a strong tell.

- AI output: "Quieres mejorar tu pricing?"  →  missing `¿`
- Native ES: "¿Quieres mejorar tu pricing?"
- AI output: "Qué sorpresa!"  →  missing `¡`
- Native ES: "¡Qué sorpresa!"

The opener does not always sit at the very start of the orthographic sentence — it sits at the start of the *interrogative/exclamative span*: "Si quieres mejorar, ¿por dónde empiezas?" The detector (`detect_inverted_marks`) checks every `?`/`!`-terminated sentence for the presence of *some* `¿`/`¡` earlier in that sentence; it is low-weight and calibrated NOT to fire on clean native prose. Register note: informal chat/SMS Spanish does legitimately drop the openers — for that register use `--type short-comms` and tolerate a higher count.

**Cleanup rule.** When cleaning AI Spanish for publication, sweep every `?` and `!` and insert the matching `¿` / `¡` at the start of the interrogative/exclamative span.

### Angle quotes (comillas latinas)

Peninsular Spanish editorial style uses `«»` (comillas latinas/angulares); much of Latin America uses curly `""`. AI defaults to straight `"X"`. Pick the convention your target locale expects and be consistent.

- AI: `"un proyecto rentable"`
- es-ES editorial: `«un proyecto rentable»`

### Accented capitals and the ñ

`Á É Í Ó Ú Ñ` at the start of words. Unlike French, modern Spanish keeps accents on capitals reliably, and `ñ` is non-negotiable. A file with stripped accents ("anos" for "años", "informacion" for "información") reads as broken Spanish on sight. If you see systematic accent loss, the file was mangled — re-accentuate before publishing.

### The raya vs the guion vs the menos

- **Guion `-`** — compound words ("teórico-práctico"), word-break.
- **Raya `—`** — dialogue and paired incise (see em-dash section). Never the Anglo spaced emphasis dash.
- **Menos `−` / en-dash `–`** — number ranges ("páginas 12–14"). Rare elsewhere.

AI conflates these. Cleanup includes replacing inappropriate "—" with "," or "(".

---

## Pedantic / escolar turns

Schoolbook Spanish. The training corpus is heavy with academic and journalistic writing, so the model defaults to phrases a *profesor de lengua* would have written in red pen on your redacción.

Banned by default:

- **"En primer lugar, conviene situar el contexto"** — meta-textual scene-setting.
- **"Cabe destacar que"** — cf. supra.
- **"No cabe duda de que"** / **"Sin lugar a dudas"** — appeal to phantom consensus.
- **"Como bien sabemos"** / **"Como es bien sabido"** — same.
- **"Llegados a este punto"** — fake academic transition.
- **"A modo de cierre"** / **"A modo de conclusión"** — fake academic closer.
- **"A primera vista"** / **"De entrada"** — AI's "at first glance" reflex (acceptable rarely).
- **"En definitiva,"** — heavy closer.
- **"El presente artículo"** / **"El presente documento"** — bureaucratic self-reference. Drop.
- **"Nos proponemos"** / **"En este artículo abordaremos"** — academic intent statement. Drop.

Rewrite by **stating** instead of **announcing**.

- Evitar: "Llegados a este punto, conviene analizar los márgenes."
- Preferir: "Ahora, los márgenes."

---

## Conclusion templates (ES)

Never start a closing paragraph with any of:

- "En conclusión,"
- "En definitiva,"
- "En última instancia,"
- "En resumen,"
- "En síntesis,"
- "En resumidas cuentas,"
- "Para concluir,"
- "Para terminar,"
- "Para finalizar,"
- "A modo de conclusión,"
- "Como hemos visto,"
- "Como se ha mencionado anteriormente,"
- "En definitiva, el futuro es prometedor,"
- "Esto es solo el comienzo."

End on a concrete action, a number, or a sharp opinion. Examples:

- "La elección depende del volumen. Menos de 100 referencias: usa A. Por encima: B."
- "Tres pasos: prueba, mide, decide. Lo demás viene solo."
- "¿No te convence? Lanza un dry-run sobre 100 líneas. Lo verás."

---

## Voice and POV tells (ES)

### Ausencia de "yo" en 800+ palabras

AI defaults to detached third-person or impersonal "se". A native author of an opinion piece **uses first person at least once per 500 words**. Cleanup rule: insert one first-person sentence per 500 words to break the impersonal register.

- Evitar (todo el texto): "Se puede observar que los márgenes bajan. Es probable que…"
- Preferir: "Veo los márgenes caer en tres clientes de cada diez. Probablemente…"

### Sobreuso del "nosotros" pedagógico

The "we" of a textbook ("vamos a ver que…"). AI defaults to this when asked to explain. Replace with "tú/usted" (direct address) or first-person singular.

- Evitar: "Vamos a ver cómo migrar."
- Preferir: "Así se migra." / "Migras en tres pasos."

### "Tú" sobreusado como dirección de marketing

The other extreme. "Tú", repeated every sentence, becomes salesy.

- Evitar: "Ganas tiempo. Ganas dinero. Ganas tranquilidad."
- Preferir: "Tres horas al día ahorradas. 2.000 € al mes salvados. Y el cliente llama menos."

### Futuro de prescripción

"Descubrirás", "comprenderás", "serás capaz de" — AI's prescriptive future. Replace with present or imperative.

- Evitar: "Descubrirás nuestros tres pilares."
- Preferir: "Tres pilares. Vamos a verlos."

### Condicional de cortesía en exceso

"Podría ser interesante", "sería conveniente" — AI's politeness-conditional. Replace with direct present/imperative.

- Evitar: "Podría ser interesante probarlo."
- Preferir: "Pruébalo."

### Voseo / tuteo / usted consistency

A Spanish piece mixing "tú" and "usted" (or peninsular "vosotros" with Latin "ustedes") within the same register is a tell of stitched-together output. Pick one address form per target locale and hold it.

---

## Tricolon rationing (ES)

Same rule as EN/FR: **cap at 1 tricolon per 200 words.** Spanish has strong rhetorical pull toward triadic structures, so a high count reads as borrowed rhythm rather than authored prose. The analyzer's `detect_tricolons` matches the "X, Y y Z" / "X, Y e Z" pattern (Spanish uses **"e"** instead of "y" before a word starting with the i-/hi- sound: "padres e hijos").

Vary list sizes (2, 4, 5 items). Use asyndeton ("rápido, fiable, limpio" without "y"). Don't close every list with ", y Z".

- Evitar: "La herramienta es rápida, fiable y precisa. Gestiona paquetes, variantes y locales. Funciona a diario, semanal y bajo demanda."
- Preferir: "La herramienta gestiona paquetes y variantes en 12 locales. Tirada diaria — o bajo demanda para una auditoría puntual."

### Sub-rule: tricolons in titles and bullets

AI title format: "Rápido, fiable y eficiente". AI bullet last item: "y escalable". Both are tricolon tells.

- Title rewrite: "Rápido. Y fiable." / "Rápido y fiable" (two items) / "Rápido" (one item).
- Bullet rewrite: drop the "y", or replace the last bullet with a different rhythm.

---

## Quick triage (for the human reviewer)

When auditing a 500-word ES piece, scan in this order:

1. Inverted marks — for every `?`/`!`, is the opening `¿`/`¡` present? If not, add it (or it flags).
2. Em-dashes / rayas — count spaced Anglo "—" in expository prose. If >1, replace.
3. Opening sentence — if it starts with a temporal abstraction ("en el mundo actual", "en la era digital") or a meta-frame ("cabe destacar"), rewrite.
4. Closing sentence — if it starts with any conclusion template ("en definitiva", "en última instancia"), rewrite.
5. Tier-1 vocab — scan; cap at 1 per paragraph.
6. AI constructions — pattern-match by eye ("no se trata solo de…, sino de…", "sumérgete en…").
7. Tricolons — count; cap at 2 per piece. Remember "y" → "e" before i-/hi-.
8. Calques — find and replace the lexical ones ("sin fisuras", "accionable", "soportar", "librería", "remover"); for translated copy scan the EN→ES table.
9. POV — at least one first-person mark if it's opinion.
10. Typography — angle quotes (locale-dependent), accented capitals, ñ, sentence-case titles; decimal comma in es-ES.

A passing ES piece, by this skill's bar:

- 0–1 spaced em-dash per 500 words.
- 0 tier-1 vocab items, ≤ 2 tier-2.
- 0 AI constructions.
- ≤ 1 tricolon per 200 words.
- Every `?`/`!` has its matching opener.
- At least one first-person mark if opinion.
- Title in sentence case.

That piece will score LOW_RISK (≤ 24) on the deterministic analyzer and survive Copyleaks / GPTZero at sub-25 % AI probability in most domains.

---

## See also

- `tells-statistical.md` — burstiness, TTR, comma density doctrine (language-agnostic)
- `tells-structural.md` — bullets, headers, tricolons, emoji
- `humanization-techniques.md` — how to write with intentional asymmetry, with Spanish worked examples
- `scripts/analyze.py` — `detect_suspect_vocab`, `detect_ai_constructions`, `detect_tricolons`, `detect_inverted_marks`
- `scripts/rules.yaml` — ES thresholds, suspect vocabulary, content-type weights
- sibling family members `human-writer-en` / `human-writer-fr` — EN + FR doctrine, same architecture

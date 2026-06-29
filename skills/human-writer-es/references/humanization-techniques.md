# Humanization Techniques

> Doctrine for the `human-writer-es` skill. The ten moves that turn AI-shaped prose into human-shaped prose. Apply in WRITE mode while drafting; apply in CLEAN mode as a targeted checklist. The doctrine is shared across the family; the worked examples are written in Spanish (EN examples kept for cross-reference).

The techniques are ordered by impact-per-edit. If you can only apply one, apply #1. If you can apply two, add #5. If you have time for everything, the full ten will cut analyzer score by 30–50 points on a typical AI draft.

Each technique below answers the same four questions:

1. **Definition.** What is it?
2. **Why it works.** Which statistical / stylistic signal does it disrupt?
3. **Worked examples.** Before and after, in EN plus ES where applicable.
4. **How to apply.** Proactive in WRITE mode, targeted in CLEAN mode.

---

## 1. Vary sentence length deliberately

**Definition.** Alternate short (≤ 6 words) and long (≥ 25 words) sentences. Aim for a standard deviation of sentence lengths ≥ 8.

**Why it works.** AI prose averages 18–22 words per sentence with a low standard deviation (typically 3–5). The analyzer measures this via `sentence_length_stdev` and flags anything under ~8. Variance is the cheapest, highest-signal humanization edit available.

### Rhythm patterns to build in

| Pattern | Shape | Use case |
|---|---|---|
| **Short-short-long** | 5w + 4w + 28w | Set up a claim, then expand |
| **Long-short** | 30w + 4w | Build then punch (very human) |
| **Fragment-long** | 2w + 25w | Topic + dump |
| **Short-medium-fragment** | 6w + 15w + 3w | Cadence variation |
| **Run-on with semicolon** | 35w with `;` | One thought, two beats |

Use semicolons to extend without resetting rhythm. Use periods to reset hard. Use commas to slow without breaking. Explicit fragments ("Eso es todo.", "Y ya.", "Punto.") are the strongest rhythm breakers.

### Worked example (EN)

Bad (uniform; lengths 13, 13, 11, 12; stdev ~1):

<!-- human-writer:ignore-start (before-example, deliberately AI) -->
> The pricing tool exports a CSV file with margin tiers per SKU. It updates daily based on competitor data scraped from major marketplaces. Users can filter by category, region, or supplier. The dashboard shows historical price evolution over the past 90 days.
<!-- human-writer:ignore-end -->

Good (varied; lengths 2, 8, 25, 18, 5, 8; stdev ~9):

> CSV out. One row per SKU, one column per marker. The pricing tool updates the file every night, pulling competitor data from Amazon, eBay, and three regional marketplaces I won't name in public. Filter it in Excel — category, region, supplier — and you get the same view our procurement team uses. Ninety days of history. That's usually enough to spot a competitor stockout.

### Worked example (ES)

Bad (uniforme; longitudes 14, 13, 15, 12; desviación ~1.2):

<!-- human-writer:ignore-start (before-example, deliberately AI) -->
> Nuestra herramienta de análisis exporta un archivo CSV para cada referencia del catálogo. Se actualiza cada noche según los datos de la competencia. Los usuarios pueden filtrar por categoría, región o proveedor. El panel muestra la evolución de los precios durante 90 días.
<!-- human-writer:ignore-end -->

Good (longitudes 3, 12, 28, 5, 18; desviación ~10):

> Exportación CSV. Una fila por referencia, una columna por marcador de precio. La herramienta corre cada noche y combina tres fuentes de datos internas más dos flujos de socios. Filtras en Excel y listo. Noventa días de histórico, que cubre casi todas las roturas de stock que vimos en 2025.

### Worked example (ES) (second pattern)

Bad:

<!-- human-writer:ignore-start (before-example, deliberately AI) -->
> El scraper recupera los datos desde el sitio de origen. Los limpia según las reglas configuradas. Los guarda en una base PostgreSQL. Los pone a disposición mediante una API REST.
<!-- human-writer:ignore-end -->

Good:

> El scraper se traga la página, la limpia con nuestras reglas caseras (que nunca sobreviven a un rediseño del objetivo) y la empuja a Postgres. Tres columnas. Ya está. La API REST saca lo demás — y dejamos la salida en JSON porque es lo que quiere el front, sin más.

### How to apply

**WRITE mode (proactive).** As you draft, force yourself to drop a one- or two-word sentence after every long one. If you've written three sentences of similar length, the next one *must* be a fragment or a 30+ word run-on.

**CLEAN mode (targeted edit).** Run `analyze.py` and look at `sentence_length_stdev`. If under 8, identify the three longest paragraphs and rewrite them by:
1. Splitting one mid-length sentence into a fragment + a sentence.
2. Joining two short sentences into one long, comma-spliced or semicolon-linked sentence.
3. Adding one explicit fragment ("Ya.", "Eso es.", "Y punto.").

---

## 2. Inject one opinion or specific anecdote per ~300 words

**Definition.** Every 300 words or so, insert one of: a first-person take, a named entity, a specific number, or a small concrete story.

**Why it works.** AI prose is information-dense but opinion-empty and entity-light. LLMs default to generic claims because generic claims minimize the chance of being wrong. Specific entities ("Rioja 2018", "47 req/s", "Marie de compras") are statistically rare in AI output; they're high-signal markers of authored prose because they couldn't be generated without first-hand context.

### What counts as an "opinion"

A take that someone could disagree with. Not "X es bueno para Y"; that's a fact-claim. But "yo me saltaría X para cualquier cosa por debajo de 100 SKUs porque el ROI no llega" is an opinion: opinionated, specific, defensible.

| Not an opinion | Opinion |
|---|---|
| "El rendimiento importa" | "El rendimiento es lo único que importa por debajo de 1k QPS; lo demás es perder el tiempo." |
| "Elige la herramienta adecuada" | "No uses Playwright para páginas estáticas. Cheerio es más rápido y mantiene menos." |
| "El pricing es importante" | "La mayoría de las estrategias de pricing fallan porque el equipo que las fija nunca habla con el que cotiza." |

### What counts as "specific"

A named entity (person, place, product, version), a date, a number with units, or a concrete event. Not "un marketplace importante"; di Amazon. Not "recientemente"; di "marzo de 2024". Not "los usuarios"; di "el equipo de compras de uno de nuestros clientes de vino".

### How to inject without breaking flow

Three placements work:

1. **Mid-paragraph aside.** "El actor (lo medimos a 47 req/s en una instancia de 2 GB) gestiona los paquetes…"
2. **End-of-paragraph kicker.** "…y así. Sinceramente, ahí es donde la mayoría se para — y donde nosotros empezamos."
3. **New sentence between two claims.** "Los clientes de API necesitan rate limits. La API de Stripe te corta a 100 req/s, por cierto. Así que diseñas alrededor de eso."

### Bad vs good (ES)

Bad (perogrullada vaga):

<!-- human-writer:ignore-start (before-example, deliberately AI) -->
> El scraping a escala requiere herramientas cuidadosamente elegidas. Elegir el framework adecuado puede marcar una diferencia significativa en el rendimiento.
<!-- human-writer:ignore-end -->

Good (postura específica):

> El caching a escala se reduce a una decisión: ¿cacheas la respuesta completa o solo los resultados caros de consulta? El cache de respuesta completa es simple (~5 líneas en nginx), pero tu hit rate se topa en torno al 40 % en cuanto varían los parámetros de consulta. El cache de resultados en Redis es más código, pero aguanta un 85 % de hit rate en nuestro tráfico. Elegimos cache de resultados para los endpoints de lectura intensiva; respuesta completa para las páginas de marketing estáticas.

### How to apply

**WRITE mode.** Before writing, list 3 specific facts/anecdotes/opinions you can drop into the piece. Place one every ~300 words.

**CLEAN mode.** Search the draft for paragraphs that contain zero proper nouns, zero numbers, and zero first-person markers. Each such paragraph needs one injection. If the draft has *none* across the whole text, that's an emergency — the piece reads as generic and no amount of sentence-length variance will save it.

---

## 3. Use asymmetric bullets

**Definition.** In any bulleted list, deliberately vary the length, structure, opening word, and grammatical shape of each item.

**Why it works.** AI bullets are parallel by default: same verb (`Construir / Construir / Construir`), same length (8–12 words each), same shape (verb + object). The analyzer flags this when > 80% of bullets share the same first or last word. Asymmetry breaks the fingerprint.

### Three asymmetry axes

| Axis | Bad (symmetric) | Good (asymmetric) |
|---|---|---|
| **Length** | All 6–8 words | Mix of 2-word fragments and 25-word callouts |
| **Opener** | All start with a verb | Mix verbs, nouns, questions, fragments |
| **Shape** | All `verb + object` | Mix commands, observations, questions, mini-paragraphs |

### Worked example (ES)

Bad (simétrico en longitud y verbo):

```
- Scrapear las páginas de producto
- Extraer los datos de precio
- Guardar los resultados en el dataset
- Exportar a CSV
```

Good (asimétrico):

```
- Parsear los ficheros de entrada (JSON directo para lo simple, parser custom para el legacy — ver `parsers.ts`)
- Importes: guardamos bruto, descuento y "total" por separado porque el formato de origen redondea a su antojo
- Datos → CSV: `make export`, y punto
- ¿Y después? La mayoría se para aquí. Nosotros lo enchufamos a Metabase para la vista de tendencia.
```

What changed: bullet 1 has a parenthetical with a code path; bullet 2 opens with a noun and uses a colon callout; bullet 3 is one short clause with an arrow; bullet 4 is a rhetorical question + two sentences.

### Sub-bullets for asymmetry

Adding a single sub-bullet under one item (and only one) breaks the visual rhythm hard:

```
- Parsear los ficheros de entrada
  - Parser custom solo para el formato legacy — añade ~200 ms/fichero
- Extracción de importes
- Exportación CSV
```

The lone sub-bullet kills the AI shape. It signals "a human chose to elaborate exactly here."

### When symmetric bullets ARE appropriate

Parallel lists where the reader compares like-with-like deserve symmetric formatting: step-by-step procedures, API reference tables, comparison matrices, pricing tiers. There, parallelism is *informational*. The rule: **prose-embedded lists should be asymmetric; reference/comparison structures can stay symmetric**.

### How to apply

**WRITE mode.** When you reach for a bullet list, draft it normally, then deliberately rewrite at least 2 of the 4 bullets to use a different shape.

**CLEAN mode.** Check `bullet_parallelism_ratio` from `analyze.py`. If ≥ 0.80, rewrite half the bullets to NOT start with the dominant verb.

---

## 4. Break tricolons: vary list sizes

**Definition.** Resist the "rule of three" reflex. Use lists of 2, 4, or 5 items. Cap the explicit three-item `y`-joined tricolon at 1 per 200 words. (Spanish uses **"e"** before an i-/hi- sound: "rápido, fiable e íntegro".)

**Why it works.** AI prose is saturated with tricolons. Typical specimens:

<!-- human-writer:ignore-start (citation: tricolon tells quoted, not used) -->
"rápido, fiable y escalable", "construir, probar y desplegar", "pequeño, mediano y grande".
<!-- human-writer:ignore-end -->

The cadence is comforting and tidy, which is exactly why LLMs default to it. The analyzer flags density above 1 per 200 words.

### Specific alternatives

| Reflex | Alternative | Example |
|---|---|---|
| Tricolon (3 items, "y") | **List of 2** | "Rápido y barato." |
| Tricolon (3 items, "y") | **List of 4** | "Rápido, barato, cacheado y auditado." |
| Tricolon | **List of 5 with asyndeton** | "Rápido, barato, cacheado, auditado, desplegable en un comando." |
| Tricolon | **List of 3 with asyndeton (no "y")** | "Rápido, fiable, escalable." |
| Tricolon | **Pair + parenthetical** | "Rápido y fiable (también barato, pero eso es de propina)." |

Asyndeton — dropping the final "y"/"e" — is the cheapest variation. It keeps the three-beat rhythm but loses the AI-signature `, y` connector.

### Worked example (ES)

Bad (tres tricolons en dos frases):

<!-- human-writer:ignore-start (before-example, deliberately AI) -->
> La herramienta es rápida, fiable y precisa. Gestiona paquetes, variantes y locales. Funciona a diario, semanal y bajo demanda.
<!-- human-writer:ignore-end -->

Good (un presupuesto de tricolon gastado; tamaños de lista variados):

> La herramienta gestiona paquetes y variantes en 12 locales. Tirada diaria, o bajo demanda para auditorías puntuales. Rápida, fiable, precisa: ese es el orden en que la optimizamos.

### How to apply

**WRITE mode.** Keep a mental "tricolon budget" of 1 per 200 words. If you've already used one, force the next list into 2 or 4 items, or use asyndeton.

**CLEAN mode.** Search the draft for `, y ` (and `, e `) followed by a noun ending the sentence. Count instances. If > 1 per 200 words, rewrite the lowest-impact occurrences first.

---

## 5. Cut all hedging openers

**Definition.** Delete the AI-templated qualifier phrases that front-load sentences. State the claim directly.

**Why it works.** Hedging openers are the most distinctive AI signature in long-form prose. They're space-filler with zero information value. Removing them is the highest words-saved-per-edit move available.

### Full forbidden list (ES)

<!-- human-writer:ignore-start (citation table: tells quoted, not used) -->
| Forbidden opener | Why it's a tell |
|---|---|
| "Cabe destacar que" | The #1 ES topic-sentence tell |
| "Cabe señalar que" | Same family |
| "Es importante destacar que" | Calque + AI template |
| "Es importante tener en cuenta que" | Calque of "keep in mind" |
| "Conviene recordar que" | Formal AI register |
| "Hay que tener en cuenta que" | Templated |
| "Sin lugar a dudas," | Empty certainty assertion |
| "En conclusión," | Conclusion template |
| "En definitiva," (as opener) | Conclusion template |
| "En última instancia," | Calque of "ultimately" |
<!-- human-writer:ignore-end -->

### Worked example (ES)

Bad:

<!-- human-writer:ignore-start (before-example, deliberately AI) -->
> Cabe destacar que el actor necesita al menos 1 GB de memoria. Es importante señalar que el rendimiento se degrada con los paquetes. Hay que tener en cuenta que el esquema puede cambiar.
<!-- human-writer:ignore-end -->

Good (opción 1, directo):

> El actor necesita 1 GB mínimo. El rendimiento baja con los paquetes (lo arreglamos en la v2). El esquema puede cambiar.

Good (opción 2, calificador en línea):

> El actor necesita 1 GB mínimo, innegociable en el plan gratis de Apify. En SKUs de paquete va un 40 % más lento; es un problema conocido para la v2. El esquema cambiará en los próximos dos trimestres.

Same content. Half the words. Sounds like someone actually wrote it.

### How to apply

**WRITE mode.** Never start a sentence with a hedging opener. If you catch yourself typing "Cabe destacar", delete and rewrite.

**CLEAN mode.** Grep the draft for every entry in the forbidden list. Delete each occurrence and rewrite the remaining sentence. This is the single highest-ROI CLEAN-mode operation.

---

## 6. Use idiosyncratic markers

**Definition.** Deliberately build 1–2 recurring tics per piece (a favored conjunction, a pet phrase, a quirky structural pattern) that the analyzer cannot fingerprint but that human readers attribute to authorial personality.

**Why it works.** Human writers have tics. AI prose is *too clean*. It avoids signature moves because LLMs are trained to produce average-of-corpus output. A deliberate tic registers as personality.

One tic per ~500 words is invisible to the analyzer (which thresholds on density) but registers to readers. Two tics per 200 words is noise.

### ES-specific tics

| Tic | Cadence | Use case |
|---|---|---|
| "Mira," as sentence pivot | 1 per ~1000 words | Pivot to a strong claim |
| "Total," as paragraph closer | 1 per ~800 words | Casual register |
| "O sea," as connector | 1 per ~400 words | Spoken register |
| "La verdad," as opener | 1 per ~600 words | First-person take |
| "Y ya." / "Y punto." as fragment | 1 per ~600 words | Hard stop after a claim |
| Sentences ending with ", vamos." | 1 per ~1000 words | Very casual register; informal only |

### Worked example (ES)

Sin tic (limpio, sabor IA):

<!-- human-writer:ignore-start (before-example, deliberately AI) -->
> La herramienta de pricing corre cada 15 minutos. Vigila 50 referencias por defecto. Los resultados llegan a una vista de Postgres que el equipo consulta desde Metabase.
<!-- human-writer:ignore-end -->

Con "Mira," y "o sea":

> La herramienta corre cada 15 minutos. Mira, probamos con 5 y los rate limits nos mataron — 15 es el suelo. Vigila 50 referencias por defecto. O sea, los resultados acaban en una vista de Postgres que el equipo consulta desde Metabase de todas formas.

The two tics are invisible to bot detection but read as a person with a voice.

### How to apply

**WRITE mode.** Before drafting, pick one or two tics. Use them at the cadence listed. Resist adding more.

**CLEAN mode.** If the piece is otherwise good but reads as bot-clean, inject *one* tic at *one* natural insertion point. Re-run the analyzer.

---

## 7. Inject digressions and parentheticals

**Definition.** Humans wander. AI stays on-track relentlessly. Insert one short digression per ~500 words. Use parentheses for genuine asides.

**Why it works.** LLMs are trained to follow the prompt without drift. The result is unnaturally focused prose: every paragraph stays inside its topical lane. Human writers tangent constantly. The drift is the signal of authentic thought. The key constraint: the digression must *return* to the main thread.

### Worked example (ES)

<!-- human-writer:ignore-start (before-example, deliberately AI) -->
Sin digresión:

> El pricing del vino es volátil. Los productores se adaptan vigilando las señales de mercado.
<!-- human-writer:ignore-end -->

Con digresión:

> El pricing del vino es volátil (el Borgoña 2020 cayó un 11 % en tres semanas). Los productores se adaptan — al menos los que miran las señales de mercado cada semana.

### Worked example (ES) (longer)

<!-- human-writer:ignore-start (before-example, deliberately AI) -->
Sin digresión:

> Una migración de base de datos necesita una buena preparación. El esquema, los índices y las restricciones — todo debe estar afinado o el despliegue revienta en producción.
<!-- human-writer:ignore-end -->

Con digresión:

> Una migración de base de datos necesita una buena preparación. Esquema, índices, restricciones — uno mal y el despliegue revienta en producción. (Lo aprendimos a las malas en una migración en marzo de 2024: esquema impecable, índices impecables, pero se nos olvidó una restricción NOT NULL en una columna llena de NULL. Rollback en 47 minutos.) Total, cinturón y tirantes en cada capa.

### How to apply

**WRITE mode.** Plan one digression per major section (every ~500 words). Mark insertion points in your outline.

**CLEAN mode.** Read each paragraph and ask: "Did the writer think of anything specific while writing this?" If every paragraph is locked to its topic, inject one parenthetical with a real specific fact.

---

## 8. Choose concrete over abstract

**Definition.** When given the choice between a generic noun and a specific one, always pick the specific. AI defaults to abstractions ("soluciones", "empresas", "flujos de trabajo"); humans default to concrete examples ("la hoja de cálculo de 14 pestañas", "el equipo de compras de nuestro cliente de vino", "la preparación del lunes por la mañana").

**Why it works.** AI prose lives in the abstraction layer because abstractions are safer. Concrete nouns ("Postgres", "el cron nocturno", "12 minutos") commit to facts that must be true. Their presence is a strong signal of first-hand writing.

### Abstract → concrete substitution table (ES)

<!-- human-writer:ignore-start (citation table: abstract AI nouns quoted, not used) -->
| Abstract (AI default) | Concrete (human alternative) |
|---|---|
| "las empresas" | "nuestro cliente de vino" / "un equipo de compras de 12 personas" |
| "soluciones" | la herramienta concreta: "el panel", "el cron", "la exportación CSV" |
| "flujos de trabajo" | el paso concreto: "la prep del lunes", "el script de importación" |
| "los usuarios" | "el comprador de Carrefour" / "el analista de la mesa de trading" |
| "los datos" | "47 columnas de SKU + precio + competidor + timestamp" |
| "el rendimiento" | "47 req/s en una instancia de 2 GB" |
| "la escalabilidad" | "lo corrimos contra 2,3 M de URLs en 9 horas" |
| "información valiosa" | "el número concreto que antes no tenías" |
| "los interesados" | nómbralos: "el director financiero", "el equipo de compras" |
| "el ecosistema" | nómbralo: "la Apify Store", "el conjunto de extensiones de Postgres" |
<!-- human-writer:ignore-end -->

### Worked example (ES)

Bad (abstracto):

<!-- human-writer:ignore-start (before-example, deliberately AI) -->
> Nuestra solución ayuda a las empresas a optimizar sus procesos.
<!-- human-writer:ignore-end -->

Good (concreto):

> Cambiamos la hoja de Excel de 14 pestañas que nuestro cliente usaba para su pricing por un solo panel. La prep del lunes por la mañana pasó de 2 horas a 12 minutos.

### Worked example (ES) (longer)

Bad:

<!-- human-writer:ignore-start (before-example, deliberately AI) -->
> La plataforma permite a las organizaciones aprovechar los datos en tiempo real para tomar mejores decisiones.
<!-- human-writer:ignore-end -->

Good:

> La plataforma empuja las variaciones de precio de 8 marketplaces a Slack, canal por canal y región por región. Cuando el Rioja 2018 baja más de un 5 %, la mesa de trading lo sabe en 90 segundos. Cerraron tres órdenes de compra el trimestre pasado con señales que la herramienta sacó antes que los correos del corredor.

### How to apply

**WRITE mode.** Each time you reach for an abstract noun ("solución", "usuarios", "datos"), pause: "What's the concrete version?" Write that.

**CLEAN mode.** Grep the draft for the abstract nouns in the table above. Replace each with a concrete equivalent or rewrite the sentence around it.

---

## 9. Vary transitions, drop the formal connectors

**Definition.** AI-generated transitions are predictable and connector-heavy. Humans transition with simple conjunctions, restructure sentences, or skip transitions entirely.

**Why it works.** The connector-class AI tells are the formal-register conjunctions below. They appear when an LLM tries to make logical structure visible at the surface, which humans rarely do.

### Forbidden transitions (ES)

<!-- human-writer:ignore-start (citation list: tells quoted, not used) -->
- Además (as paragraph opener)
- Asimismo
- Igualmente
- Por consiguiente
- Por ende
- Por lo tanto (as paragraph opener)
- No obstante (when overused)
- Por otra parte (as paragraph opener)
- De igual manera
- En este sentido (as paragraph opener)
<!-- human-writer:ignore-end -->

### ES alternatives

- **"Y"**: yes, start a sentence with "y". Spanish allows it.
- **"Pero"**: sharp pivot.
- **"Aunque"**: informal contrast.
- **"La cosa es que"**: register varies but this is human.
- **"Bueno,"** / **"Total,"**: Spanish rhythm markers.
- **"Si no,"**: branching alternative.
- **Restructure**: often the cleanest transition is no transition — rewrite the next sentence to flow without a connector.

### Worked example (ES)

Bad (cargado de conectores):

<!-- human-writer:ignore-start (before-example, deliberately AI) -->
> El actor recupera los precios de Amazon. Además, vigila los niveles de stock. Asimismo, se integra con Slack. Por otra parte, admite exportaciones diarias.
<!-- human-writer:ignore-end -->

Good (variado):

> El actor recupera los precios de Amazon. También vigila el stock. La integración con Slack llega en la v2. Exportaciones diarias — u horarias si lo pides.

### How to apply

**WRITE mode.** Never use the forbidden list. At a transition point, pick from the human alternatives or restructure.

**CLEAN mode.** Grep for every forbidden transition. Delete and rewrite. One of the fastest, highest-impact CLEAN-mode operations.

---

## 10. Build in productive imperfection

**Definition.** Humans pause, repeat for emphasis, change midstream, use casual contractions and oral elisions. AI hyper-corrects. A light imperfection ratio (1–2 instances per 500 words) registers as human without seeming sloppy.

**Why it works.** LLMs are trained out of the small imperfections real writing carries. Self-corrections, repetitions for emphasis, and casual interjections are statistically scarce in AI output and common in human prose. A small dose flips the signal.

### Imperfection categories (ES)

| Category | Example | Cadence |
|---|---|---|
| **Oral elisions / contractions** | "pa'" for "para" (very informal only), "to'" (extreme) | Extreme cases — informal marketing only, never technical |
| **Repetition for emphasis** | "Está bien. Muy bien." | 1 per ~500 words |
| **Self-correction** | "El precio se movió un 11 % — bueno, más bien 12 % si cuentas las comisiones." | 1 per ~700 words |
| **Casual interjections** | "La verdad,", "Mira,", "Oye,", "Bueno," | 1 per ~400 words (overlaps with #6) |
| **Mid-sentence pivot** | "Probamos el proxy más barato, pero — en fin, ya te imaginas." | 1 per ~800 words |
| **Trailing "y tal"** | "…o lo que sea en tu stack, y tal." | 1 per ~1000 words (informal only) |

### Worked example (ES)

<!-- human-writer:ignore-start (before-example, deliberately AI) -->
Sin imperfección (IA hipercorrecta):

> El precio se movió un 11 % en tres semanas. Esto es significativo. Conviene investigar la causa subyacente.
<!-- human-writer:ignore-end -->

Con imperfección (autocorrección + interjección):

> El precio se movió un 11 % en tres semanas — bueno, más bien 12 % si cuentas las comisiones. Eso es mucho. La verdad, merece que lo miremos.

### Calibration warning

Imperfection is dosed. Too much and you cross from "human writer" to "sloppy draft". The cadences above are upper bounds. In a technical doc, lean low. In casual marketing copy, the upper end works.

### How to apply

**WRITE mode.** Use natural elisions where the register allows. Add one self-correction or casual interjection per ~500 words.

**CLEAN mode.** Identify one paragraph that reads as too-polished and inject a single self-correction.

---

## Bonus: how to combine techniques

The techniques compound. Applying #1 alone drops `sentence_length_stdev` flags. Applying #1 + #5 + #9 drops the three most common AI signatures simultaneously. Below is a worked example showing the cumulative effect on a Spanish paragraph.

### Starting paragraph (vanilla AI output, ~90 words)

<!-- human-writer:ignore-start (citation: deliberately AI) -->
> En el mundo actual del comercio electrónico, vigilar los precios de la competencia es fundamental. Nuestra herramienta de inteligencia de precios ofrece una solución fluida, robusta e intuitiva. No se trata solo de seguir precios, sino de empoderar a tu equipo con información accionable. Ya seas una startup o una gran empresa, nuestra plataforma te ayuda a navegar la complejidad del pricing dinámico. Además, se integra sin fisuras con tus flujos de trabajo. En definitiva, podrás tomar decisiones basadas en datos y adelantarte a la competencia.
<!-- human-writer:ignore-end -->

**Analyzer baseline:** suspect vocab ~7 (`en el mundo actual`, `fundamental`, `fluida`, `robusta`, `empoderar`, `accionable`, `sin fisuras`), tricolon 1 ("fluida, robusta e intuitiva"), construction "no se trata solo de … sino de", "ya seas … o", conclusion "en definitiva", connector "además". Estimated AI-probability: HIGH/CRITICAL.

### Final humanized version (same content, ~90 words)

> Los precios cambian cada hora en Amazon en plena campaña de Navidad. Mira — nuestra herramienta corre cada 15 minutos contra tus 50 SKUs más caros y marca cualquier movimiento mayor del 3 %. Y ya. El panel es una vista de Postgres (sin UI bonita) porque el equipo que lo necesita vive en Metabase de todas formas. Lo montamos para un minorista mediano en 2024, después de que les bajaran el precio seis semanas seguidas antes de enterarse. Si quieres el mismo montaje, son unas 200 líneas de Python en un cron. Pon tus propias categorías.

What changed: temporal abstraction → concrete season + marketplace; tricolon and suspect vocab gone; "no se trata solo de…" and "ya seas…" gone; "en definitiva" gone; "además" gone; added a "Mira —" tic, a "Y ya." fragment, a real 2024 anecdote, concrete numbers (15 min, 50 SKUs, 3 %), and a closing pointer.

### Order of operations summary

| Order | Technique | Reason |
|---|---|---|
| 1 | #5 Cut hedging openers | Highest words-saved, fastest fix |
| 2 | #9 Vary transitions | Cuts the connector class in one pass |
| 3 | #1 Vary sentence length | Statistical signal most analyzers test |
| 4 | #4 Break tricolons | Density signal — easy to target |
| 5 | #3 Asymmetric bullets | Only if the piece has lists |
| 6 | #8 Concrete over abstract | Compounds with #2 |
| 7 | #2 Inject opinion/anecdote | Highest authorial-signal move |
| 8 | #7 Digressions | Adds drift |
| 9 | #6 Idiosyncratic markers | Final personality layer |
| 10 | #10 Imperfection | Final humanity layer |

The first five fix the statistical signature. The last five inject the authorial signal.

---

## See also

- `tells-stylistic-es.md` — Spanish vocabulary and construction lists that techniques #5, #8, #9 reference directly.
- `tells-statistical.md` — the metrics (sentence-length stdev, bullet parallelism, tricolon density, em-dash density) these techniques target.
- `tells-structural.md` — bullet, header, conclusion anti-patterns that techniques #3 and #4 disrupt.
- `adapter-marketing.md` / `adapter-short-comms.md` / `adapter-technical.md` / `adapter-editorial-seo.md` — content-type-specific calibration.

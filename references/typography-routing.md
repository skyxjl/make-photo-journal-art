# Theme-Driven Typography Routing

Treat typography as part of the story, not a fixed trait of a layout template. Resolve a type system from the user's exact subject before composing, even when the user selected a named style family.

## Precedence

Choose typography in this order:

1. Explicit user wording or supplied type reference.
2. Cultural, historical, regional, and genre fit of the subject.
3. Emotional tone and photographic character.
4. Default typography of the selected visual family.

The theme may override a family's default display type without replacing the family's surface, layout, photo treatment, or decoration system. For example, a Fujifilm-inspired album about a beach weekend may use a clean humanist sans title, while the same album structure about Yungang Grottoes should use a Northern Wei stele-inspired display title.

Never let `日系`, `杂志`, `胶片`, `手帐`, or a reference image force the same headline font onto unrelated subjects.

## Build a typography brief

Resolve these fields before writing the image-generation prompt:

- **Theme signals:** place, era, culture, activity, genre, audience, and source-image forms.
- **Title voice:** monumental, literary, playful, technical, commercial, intimate, youthful, ceremonial, or documentary.
- **Display construction:** serif/sans/handmade/calligraphic/inscriptional; width; weight; stroke character; terminal shape; contrast; texture.
- **Body voice:** highly legible Song/Ming serif, humanist sans, geometric sans, neo-grotesk, rounded sans, typewriter, or restrained handwriting.
- **Utility voice:** captions, numerals, dates, Latin labels, routes, indexes, and seals.
- **Hierarchy:** title scale and line breaks, deck, body, labels, numerals, spacing, alignment, and contrast.
- **Material behavior:** flat ink, carved/debossed stone, screen print, marker, offset halftone, glossy label, film-caption imprint, or clean digital print.
- **Forbidden mismatch:** type treatments that would trivialize, exoticize, age, or contradict the subject.

Use at least two coordinated voices: one expressive display voice and one readable text/utility voice. Do not set the whole page in a decorative display face.

## Subject routing examples

These are routing examples, not rigid presets. Refine them from the photos and user's tone.

### Chinese historical sites and material heritage

- Derive the display voice from the correct period and medium when known: inscription, stele, seal, manuscript, woodblock, architectural plaque, or carved cliff.
- Keep body copy in a calm, readable Song/Ming serif or restrained humanist sans.
- Use material effects sparingly and consistently with the site: shallow carved edge for stone, restrained vermilion seal for inscription culture, mineral-pigment accents for murals.
- Do not use one generic brush-calligraphy treatment for every dynasty or heritage site.

**Yungang / Northern Wei example:** monumental Northern Wei stele and cliff-inscription character; square structure, broad horizontal strokes, angular chisel-cut terminals, restrained asymmetry, limestone/ivory ink, optional small cinnabar seal; body in refined Song/Ming serif. Avoid cursive brush script, faux-temple novelty lettering, and ordinary Japanese magazine Mincho as the main headline.

### Classical gardens, poetry, museums, and literary travel

- Prefer a refined Song/Ming serif, restrained seal-script accent, or elegant inscriptional display depending on the actual era and object.
- Use generous rhythm and quieter weight; keep long text especially readable.
- Avoid making `Chinese culture` automatically equal to flamboyant cursive calligraphy.

### Mountains, lakes, forests, and quiet nature

- Use an organic but controlled serif, humanist sans, or lightly hand-drawn display with open spacing.
- Echo terrain or vegetation through line length, verticality, or stroke taper rather than literal leaf-shaped letters.
- Avoid heavy monumental type unless the user's language calls for awe, geology, expedition, or grandeur.

### Seaside, summer, camping, and bright leisure

- Use an airy geometric or humanist sans, wide tracking, compact editorial labels, and clear numerals.
- A handwritten accent may feel casual, but keep the main title crisp if the visual family is cinematic or editorial.
- Avoid heritage-style carved or antique display faces.

### City guide, architecture, market, and food trail

- Use bold condensed sans or sturdy neo-grotesk for navigation and sectioning; pair with compact readable captions.
- Let visible signage, packaging, menus, tiles, facades, or transit systems influence width, color, and modular rhythm without copying brands.
- Food can support warmer, rounder display forms; architecture can support sharper grids and high-contrast editorial serif.

### Family, children, pets, and playful everyday life

- Use friendly rounded sans, soft hand lettering, or cut-paper forms with large counters and simple shapes.
- Preserve dignity and readability; do not default to childish bubble letters when the mood is tender or documentary.

### Film, music, books, fandom, and nightlife

- Route from the work's genre and era: cinematic serif, poster grotesk, photocopy zine lettering, typewriter, or restrained handwritten annotation.
- Never imitate a protected logo or title treatment exactly; create a genre-compatible original system.

### Route-map memo and information diary

- Use condensed sans for headers, monospaced or tabular numerals for stops and dates, and a controlled handwritten voice only for short personal annotations.
- Prioritize scanning and factual hierarchy over decorative expression.

### Vintage, archive, and historical family records

- Use age-appropriate typewriter, letterpress serif, utilitarian grotesk, or restrained handwriting only when the visual family genuinely calls for aging.
- Do not add fake antiquity to contemporary photos merely because the user says `胶片` or `怀旧`.

## Theme adaptation inside each style family

The style family supplies the **typographic medium**, while the theme supplies the **voice**.

- **Glossy digital scrapbook:** keep glossy labels, energetic scale changes, and crisp digital finish; adapt display forms to the subject.
- **Handmade vintage fandom:** keep analog handwriting/cut-print material, but route its era and genre from the actual fandom or trip.
- **Clean modern archive:** keep restrained hierarchy; adapt serif/sans character to documentary, literary, family, or cultural content.
- **Fujifilm cinematic album:** keep minimal flat photo-book integration; select a theme-aware title when a title is required instead of always using tiny Japanese lifestyle labels.
- **Crisp Japanese editorial:** keep grid discipline and editorial scale; the headline may become inscriptional, architectural, culinary, playful, or technical according to the subject.
- **1990s catalog:** keep commercial print and indexed utility text; adapt product-category voice without copying brands.
- **Calendar sticker board:** keep functional numerals and date clarity; adapt only the display month/theme title and annotations.
- **Marker zine:** keep handmade paint/marker material; vary stroke energy, width, and letterform mood by subject.
- **Route-map memo:** keep navigational legibility; adapt header and landmark-label voice to location and trip character.

## Prompt language

Include a dedicated block in the image-generation request:

```text
Typography brief:
- Theme rationale: <why this type system belongs to the subject>
- Display title: <construction, weight, width, stroke character, material, line breaks>
- Body: <readable family, size relationship, leading, line length, contrast>
- Labels/numerals: <utility family and role>
- Exact text: "<verbatim title>"; "<verbatim short labels>"
- Forbidden mismatch: <generic or culturally wrong typography to avoid>
```

Describe visual properties rather than relying only on a named font. If a user specifies a font, preserve it when available; otherwise translate it into observable traits.

## Text length and rendering

- Keep image-model text short whenever possible.
- For a title, choose line breaks deliberately around semantic units; never split a name or fixed phrase awkwardly.
- Set paragraphs in the body voice, not the display voice.
- Reserve a clean high-contrast panel for long copy and use deterministic text overlay when available.
- Treat misspellings, pseudo-characters, missing sentences, and culturally incorrect letterforms as quality failures.

## Typography QA

Before accepting an output, verify:

1. Could the title plausibly belong to this specific subject, not just this layout template?
2. Does the display treatment reflect the correct culture/era/genre without caricature?
3. Are title, body, labels, and numerals clearly differentiated but coordinated?
4. Is the title exact, legible, and broken into intentional lines?
5. Is body copy readable at output size with adequate contrast and leading?
6. Are material effects restrained and logically tied to the subject?
7. Would swapping in unrelated travel photos make the typography feel wrong? If not, the routing is still too generic.


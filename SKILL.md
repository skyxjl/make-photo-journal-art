---
name: make-photo-journal-art
description: Create or revise finished raster journal, scrapbook, memory-board, diary-collage, photo-journal, monthly-recap, editorial-journal, and 手帐 images from user-supplied photos plus a short or detailed description. Use when a user asks to 把照片做成手帐、旅行手帐、拼贴日记、月度回顾、观影手帐、照片日记、scrapbook, journal spread, memory collage, or wants one of the bundled layout styles adapted to their own subject, colors, mood, and factual text.
---

# Make Photo Journal Art

Turn user photos into a complete, art-directed journal image. Treat the photos as the source of truth, the user's description as the emotional direction, the selected **style family** as the surface/graphic language, and the selected **layout structure** as geometry only. Adapt palette and supporting elements to the actual input; never hardcode a seaside, mountain, film, outdoor, vintage-paper, or aged-notebook treatment merely because a reference uses one.

Use the `imagegen` skill and built-in image generation tool for all raster generation and editing. Follow its image inclusion, local-file inspection, output, and validation rules.

## Start the interaction

Inspect the supplied photos before asking questions. Then infer whether the user has already provided enough direction.

- If the request is sufficiently specific, do not ask the user to choose a mode; proceed with the apparent level of control.
- If the user only asks to “make this into a journal/scrapbook,” offer two paths in one short question:
  - **Simple mode:** the user gives a theme or feeling; AI decides layout, palette, copy, and supporting elements.
  - **Custom mode:** the user controls any desired fields; AI fills all omitted fields.
- Ask at most 1–3 short questions in one round, and only when missing information materially changes the result.
- Do not turn custom mode into a mandatory questionnaire.

Read [input-modes.md](references/input-modes.md) when deciding what to request, what to infer, or what facts need confirmation.

## Analyze the inputs

Before generation, verify the real image container format rather than trusting the filename extension. Some iPhone `.jpg` files are MPO containers and are rejected by image-editing APIs. If an input reports MPO or another unsupported container, create a temporary ordinary RGB PNG from its first frame without modifying the original, then use that PNG as the generation input.

For every photo, identify:

1. The likely primary subject and protected areas such as faces, hands, pets, meaningful objects, and readable signs.
2. Scene, activity, season, time-of-day cues, recurring objects, and visual motifs.
3. Dominant and accent colors, lighting, texture, and emotional tone.
4. Which photo should lead, which support, which may be cropped or cut out, and whether any are redundant or unsuitable.
5. Facts visible in the photo versus interpretations that must remain non-factual.
6. Cutout-sticker candidates: people, pets, food, vehicles, instruments, flowers, or distinctive objects with separable silhouettes and enough edge detail.

Prefer 1–5 primary photos for a single generated composition. If the user supplies more, either select the strongest set when permission is implicit, propose multiple pages, or ask which are mandatory. Never silently discard a photo the user explicitly marks as required.

## Build the creative brief

Internally resolve these fields even if the user provides only one sentence:

- subject/story
- mood
- layout family
- output format and aspect ratio
- primary and supporting photo roles
- palette extracted from the photos plus at most one deliberate accent color
- material language such as paper, print, tape, ink, film, or clean digital collage
- age level: pristine/modern, lightly tactile, or deliberately vintage
- photographic treatment such as natural digital, Fujifilm-inspired Japanese film, monochrome archive, or retro halftone
- background enrichment plan derived from source-photo colors, textures, silhouettes, objects, signs, patterns, and environmental fragments
- theme-driven typography brief covering cultural/period/genre fit, display voice, body voice, utility labels, hierarchy, material behavior, and forbidden mismatch
- decoration density
- supporting motifs derived from scene + activity + season + mood
- exact factual text
- AI-authored expressive text
- invariants and avoid list

When helpful, state the direction in one sentence and continue immediately. Do not wait for approval unless the brief contains uncertain facts, conflicting constraints, substantial identity transformation, or lots of exact text.

## Separate style from layout

Read [style-families.md](references/style-families.md) before composing. Resolve two independent decisions:

1. **Style family controls:** substrate/background, age level, image edge treatment, typography, graphic marks, palette behavior, print/digital finish, and decoration vocabulary.
2. **Layout structure controls:** single page or spread, grid or free placement, density, hierarchy, binding/seam, and photo count.
3. **Photographic treatment controls:** highlight roll-off, shadow hue, skin tone, contrast, saturation, grain, and consistency across source photos. It may be reused across multiple visual families.

When the user supplies both a mode and a layout, the mode is the primary visual authority. For example, `彩色手绘主题日记 + 高密度双页剪贴` means a bright marker-zine visual system arranged across a dense spread; it does **not** mean an aged cream scrapbook with generic torn kraft paper.

A user may combine styles. Preserve the complete visual fingerprint of the primary style and borrow no more than two named traits from a secondary style. Never average all families into generic scrapbook aesthetics.

Do not equate a clean or modern style with empty space. Build at least three visual layers when the reference is information-rich: primary photos/cutouts, secondary source-derived graphics or fragments, and tertiary typography/routes/patterns. Leave intentional breathing pockets, not large unassigned blank regions.

The bundled reference images define a complete visual system—not composition alone. Match their relationships among background, age, color, image edges, typography, density, and decoration while replacing their people, brands, copyrighted characters, wording, and subject matter with the user's content.

## Separate truth from invention

Require user-provided or clearly visible evidence for:

- dates, locations, names, relationships, anniversaries, routes, event names, brands, titles, and other factual claims
- long quotations or attributed text

AI may create:

- non-factual titles and mood lines
- decorative labels and category words
- relevant visual motifs, paper ephemera, abstract marks, stamps, doodles, and invented non-branded tickets
- color, hierarchy, crop, frame, and layout decisions

Use emotionally true but factually neutral language when facts are absent. For example, prefer “A Day to Keep” over “Our Third Anniversary.” Never infer sensitive experiences or relationships from appearances.

## Compose the image-generation request

Read [prompting-and-qa.md](references/prompting-and-qa.md). Use the `style-transfer` or `compositing` imagegen taxonomy as appropriate.

Explicitly label every input image's role. State:

- which source photos must appear
- which photo is the lead
- whether faces and identity must remain recognizable
- whether cropping, cutouts, recoloring, illustration, or background changes are permitted
- the layout family's structural rules
- the dynamically inferred palette and motifs
- exact short text in quotation marks
- protected areas and avoid items
- which subjects should become cutout stickers and where they may cross page, frame, or canvas edges
- which source-derived details should enrich the background and at what opacity/scale
- the chosen photographic treatment and the invariants for skin tones and source color

Preserve user photos as photographs by default. Allow non-destructive crop, color harmonization, paper framing, and collage overlap. Do not redraw people, change clothes, add people, or replace backgrounds unless requested or clearly permitted.

## Use cutout stickers intentionally

Read the cutout guidance in [prompting-and-qa.md](references/prompting-and-qa.md). When the selected visual family permits stickers or cutouts, prefer 1–3 source-derived cutout stickers over generic decorative stickers. Use them to activate page edges, bridge photo modules, and create foreground depth. Preserve the original subject's identity and proportions; never synthesize a replacement person merely because a cutout is requested.

## Handle typography

Read [typography-routing.md](references/typography-routing.md) for every composition that contains text. Do this even when the user has already selected a visual family: the style family controls typographic medium and layout behavior, while the subject controls the actual voice.

Build a typography brief from place, era, culture, activity, genre, emotion, source-image forms, and the user's wording. Use this precedence: explicit user request > subject authenticity > mood/photo character > style-family default. A selected style must not force the same title face onto unrelated themes.

Use at least two coordinated roles: an expressive display title and a highly readable body/utility voice. Specify observable traits—structure, weight, width, stroke character, terminals, spacing, material, line breaks, and contrast—rather than relying only on a font name. Never use generic brush calligraphy merely to signal “Chinese,” or generic Japanese editorial lettering merely because the layout is Japanese-inspired.

Keep model-rendered text short when possible. Prefer a title, date/location if supplied, and 1–3 short labels. Spell exact text verbatim in the prompt.

- For long accurate body copy, calendar dates, indexes, or magazine layouts, generate the visual base with reserved text regions and add exact typography in a deterministic layout step when available.
- If no deterministic layout mechanism is available, shorten the copy with user approval or explain the limitation; do not pretend garbled text is acceptable.
- Do not fill negative space with pseudo-English or illegible handwriting.

## Generate and inspect

1. Generate one strongest composition by default. Generate variants only when requested or when comparing directions is the task.
2. Inspect the result for photo inclusion, identity fidelity, hierarchy, theme relevance, text accuracy, and fidelity to the selected style fingerprint.
3. Verify that the typography belongs to the specific topic, culture, era, genre, and mood rather than merely matching the page template.
4. Check that embellishments come from the input story rather than the reference image's subject.
5. Check that faces and essential objects are not hidden by tape, stickers, text, binding, or crops.
6. Iterate once with a targeted correction when a correctable defect is visible.
7. Return the image inline and summarize the chosen direction, exact text used, and any material limitation.

## Revise naturally

Accept follow-ups such as “贴纸减半,” “保持版式换成绿色,” “主图换第二张,” or “去掉英文.” Change only what the user requests and preserve the rest of the approved composition. Repeat identity and content invariants on every image edit.

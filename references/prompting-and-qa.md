# Prompting and Quality Assurance

## Normalize image inputs

Check the underlying image container before calling image generation. Do not rely on `.jpg` or `.jpeg` extensions: iPhone portrait and Live Photo exports may decode as multi-frame MPO even when named `.jpg`, and the image-generation edit endpoint may reject them.

- Preserve the original file.
- Convert only unsupported inputs to a temporary ordinary RGB PNG using the first frame.
- Keep orientation and pixel dimensions.
- Verify the temporary output reports `PNG image data` before passing it to image generation.
- Remove or ignore the temporary copy after the task; never overwrite the user's photo.

When Pillow is available, an equivalent normalization is `Image.open(src).convert("RGB").save(dst, format="PNG")`.

## Prompt scaffold

Use only relevant lines:

```text
Use case: compositing or style-transfer
Asset type: finished photo journal / scrapbook image
Primary request: transform the supplied source photos into a complete journal composition about <story>
Input images: Image 1 = lead source photo; Image 2 = supporting source photo; ...
Source invariants: preserve <faces, identity, clothing, pets, key objects>; all required source photos must remain recognizable
Layout family: <family name and structural grammar>
Typography brief: theme rationale; display construction; body voice; labels/numerals; hierarchy; material behavior; forbidden mismatch
Composition: <page format, hierarchy, binding, crop, overlap, negative space>
Mood: <emotional direction>
Color palette: extract <colors> from source photos; add <accent> only if useful
Photographic treatment: <natural contemporary / Fujifilm-inspired Japanese film / documentary monochrome / retro halftone>
Materials: <paper, tape, print, film, ink, crayon, shadows>
Age level: <pristine modern / lightly tactile / deliberately vintage>
Forbidden style leakage: <materials and traits belonging to other families>
Background enrichment: <large low-opacity source crop; medium abstractions; small source-derived icons/cards/patterns>
Coverage targets: <photos/cutouts %; graphics/type %; true breathing space %>
Supporting motifs: derive from <scene + activity + season + mood>; include <motifs>
Text (verbatim): "<short exact title>"; "<short exact label>"
Permitted transformations: <crop, cutout, harmonize color, frame, illustration if allowed>
Constraints: do not hide faces or key objects; do not introduce factual claims
Avoid: pseudo-text, watermark, irrelevant stickers, copied reference subjects, brand logos, duplicated people, malformed hands
```

For simple mode, keep this brief and let the model make aesthetic choices. For low-autonomy custom mode, encode all supplied constraints and do not embellish beyond them.

## Pre-generation fingerprint lock

Before writing the final image prompt, state these seven decisions internally and make them mutually consistent:

1. `Primary visual family`
2. `Layout structure`
3. `Surface/background`
4. `Age level`
5. `Photo edge treatment`
6. `Theme-driven typography system` (display, body, utility, rationale, forbidden mismatch)
7. `Allowed decorations / forbidden leakage`
8. `Photographic treatment`
9. `Background layer plan and coverage targets`

Example:

```text
Primary visual family: bold marker-and-cutout zine diary
Layout structure: dense two-page spread
Surface: flat pale printed form paper
Age level: youthful handmade, not vintage
Photo edges: clean contour cuts and a few flat rectangles
Typography: broad marker title plus integrated handwriting
Allowed: opaque marker blocks, underlines, stars, 1–2 tape strips
Forbidden leakage: cream fibrous notebook, leather cover, dried botanicals, map collage, Polaroid grid, sepia wash, heavy shadows
```

Do not proceed with an internally vague label such as “handmade scrapbook aesthetic.” It invites generic old-notebook output.

## Build three background layers

For Japanese editorial, route memo, glossy digital, calendar, marker-zine, and other information-rich families, specify all three layers:

1. **Primary layer:** main photographs and large cutout subjects.
2. **Secondary layer:** source-derived environmental crops, object cutouts, landmark silhouettes, color fields, texture echoes, caption cards, or small photo thumbnails.
3. **Tertiary layer:** routes, icons, micro-labels, rules, dots, patterns, arrows, calendars, coordinates only when verified, and small handwriting.

Use opacity and scale to preserve hierarchy. Secondary content may be large but faint; tertiary content should be small and rhythmic. Do not solve emptiness by enlarging generic icons or adding random stickers.

For route memo, aim for at least 7–12 distinct non-photo information elements in addition to the route: e.g. 3–5 source-specific icons, 2–3 cards, 1–2 landmark/object line drawings, and several labels or micro-patterns.

For crisp Japanese editorial, aim for at least 2–4 source-derived cutouts or cropped fragments beyond the main photos, plus caption blocks/rules that occupy the grid. A large white region must have an editorial purpose such as headline, deck, pull quote, or cutout subject.

## Photo roles

Assign one role to every source image:

- **lead:** largest emotional or narrative anchor
- **supporting:** establishes place, activity, detail, or sequence
- **cutout candidate:** person, pet, food, or object that benefits from contour extraction
- **texture/detail:** close-up usable in a small frame
- **optional:** may be omitted only if not marked mandatory

Do not ask an image model to treat all photos as equally large unless the chosen grid specifically requires it.

## Source-derived cutout stickers

Use cutout stickers to make compatible layouts more lively. Select 1–3 candidates from the user's photos rather than inventing unrelated sticker characters.

Good candidates:

- a full or three-quarter person with visible silhouette
- a pet, bowl of food, flower, vehicle, instrument, souvenir, or distinctive object
- an action figure whose pose can point into the composition

Treatment options:

- **Glossy digital scrapbook / calendar:** precise contour, 6–14 px-equivalent clean white border, optional colored secondary keyline, crisp light shadow.
- **Marker zine:** contour cut with no border or a rough marker outline, almost flat with minimal shadow.
- **Japanese editorial:** clean borderless cutout, flat print overlap, little or no shadow.
- **Route-map memo:** small clean white-bordered cutout attached to a route node or page corner.
- **Vintage fandom:** tan/paper-colored outline with analog pasted edge.

Edge placement:

- place one cutout so 5–15 percent crosses the outer canvas edge, page edge, or color field
- let another bridge two modules or overlap a frame corner
- use pose and gaze to point inward, not out of the composition
- keep the head and identity-bearing features inside the safe canvas unless intentional clipping is requested
- never place a face, hand, pet head, or meaningful object under the center binding

Avoid cutting around hair, fingers, hats, instruments, or transparent objects carelessly. Preserve proportions and original identity. Do not generate a new lookalike person. Do not repeat the same cutout more than once unless the user asks for a sticker-sheet effect.

Cutouts are normally allowed in families 1, 2, 5, 7, 8, and 9; optional and restrained in family 6; normally prohibited in families 3 and 4.

## Surface fidelity

Do not request physical scrapbook realism unless the selected style actually uses it. First name the intended surface system:

- crisp digital collage
- flat magazine print
- modern photo book
- lightly tactile handmade page
- deliberately aged analog scrapbook
- retro commercial halftone print
- flat marker/photocopy zine

For genuinely handmade layouts, request only the physical traits present in that family:

- consistent overhead viewpoint
- believable paper thickness and page edges
- restrained cast shadows with one light direction
- tape and paper pieces that appear attached rather than floating
- small imperfections in alignment, cuts, folds, and ink
- a clear hierarchy beneath the decorative density

For flat editorial, calendar, catalog, and zine families, explicitly suppress heavy shadows, thick paper depth, pervasive tape, torn edges, bindings, yellowing, and fibrous craft paper.

Avoid excessive bevels, fake 3D depth, or objects that pierce through bindings. Glossy stickers are correct for family 1 and family 7 but incorrect as a universal treatment.

## Text strategy

Image models handle short display text better than paragraphs.

Read [typography-routing.md](typography-routing.md) before locking the prompt. Treat the style family's typography as a medium, not a universal font choice. The theme may override its default display voice while preserving the family's grid, surface, depth, and decorations.

- Keep generated-in-image text to a title and 1–3 labels.
- Quote exact text verbatim and state language.
- Reserve clean regions for long user copy.
- For a true calendar, numbered catalog, or magazine article, add exact text with deterministic layout after generating the visual base.
- Reject meaningless filler writing as a quality defect.

## Inspection checklist

After generation, verify:

### Source fidelity

- every mandatory image is present
- the lead image is actually dominant
- faces, pets, clothing, and important objects remain recognizable
- no person or limb is duplicated or merged
- no binding, tape, sticker, or title obscures a protected area
- cutout stickers preserve the exact source identity, silhouette logic, and proportions

### Design

- layout follows the selected structural family
- substrate, age level, edge treatment, typography, decoration vocabulary, and print/digital finish match the selected visual fingerprint
- the output does not leak generic aged-notebook traits from unrelated families
- edge cutouts create intentional movement without accidental clipping or outward-facing visual flow
- information-rich styles meet their coverage targets and contain meaningful secondary and tertiary layers derived from the source photos
- requested photographic treatment is visible across all photos without damaging skin tone or highlight detail
- palette comes from the supplied photos and supports the requested mood
- supporting motifs relate to scene + activity + season + mood
- the composition has a clear entry point and reading path
- decoration density matches the requested level
- collage materials share consistent lighting and perspective

### Truth and typography

- all factual text matches user input
- no invented location, date, relationship, brand, or event
- exact short text is legible and spelled correctly
- the title voice fits the specific culture, period, place, genre, and mood rather than only the layout family
- display, body, labels, and numerals form a coordinated hierarchy instead of using one decorative face everywhere
- line breaks preserve semantic units and long copy remains readable
- inscription, brush, typewriter, marker, carved, or distressed effects have a subject-based reason
- no pseudo-English, watermark, or accidental logo

### Correction priorities

If a revision is needed, correct in this order:

1. missing or altered people/photos
2. obscured faces or key subjects
3. wrong factual text
4. culturally or thematically mismatched typography
5. incorrect layout structure
6. irrelevant motifs or wrong palette
7. minor decoration and texture issues

Make one targeted revision at a time and repeat all invariants.

## Style-collapse audit

Treat any of the following as a failure when they appear across unrelated requested styles:

- repeated warm-ivory or yellowed background
- the same leather-bound or spiral notebook mockup
- torn kraft-paper borders on nearly every photo
- masking tape on every image
- dried plants and map fragments regardless of subject
- identical sepia/olive color grading
- heavy analog grain presented as “Fujifilm” or “Japanese” by default
- Polaroid grids used for editorial, full-bleed, calendar, or zine families
- the same generic Japanese-magazine headline, brush script, or handwritten title reused across unrelated subjects
- faux “Asian” novelty lettering or indiscriminate calligraphy for Chinese heritage topics
- broad unassigned blank regions in Japanese editorial or route memo outputs
- route memo pages with only a sparse path and generic icons
- interpreting Fujifilm-inspired color as sepia paper, dust, light leaks, date stamps, or retro ephemera

When two outputs using different primary families could swap their photos and still look like the same template, the styles are insufficiently differentiated. Revise the surface, edge treatment, typography, graphic medium, and depth model—not merely the colors or stickers.

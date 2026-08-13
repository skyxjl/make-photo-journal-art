# Input Modes

## Simple mode

Require only:

1. One to five primary photos.
2. One sentence describing the theme, story, or feeling.

Treat intended use or aspect ratio as optional. Infer it from the request and photo orientation when absent.

Example:

> 简单模式。用这些照片记录我们秋天去山里散步，温暖、安静一点。

AI decides:

- primary visual style
- layout structure
- lead photo
- crop and supporting-photo treatment
- palette and accent color
- surface system, age level, and print/digital finish
- photographic treatment, including Fujifilm-inspired Japanese film when requested
- background enrichment derived from the photos rather than generic filler
- decoration density
- theme-matched title, body, label, numeral, and annotation typography
- relevant motifs
- 1–3 source-derived cutout stickers when the selected style supports them
- non-factual title and short copy
- aspect ratio when not specified

Simple-mode defaults:

- preserve faces, identity, clothing, and key subjects
- allow crop, cutout, color harmonization, photo borders, and overlap
- derive palette from the photos
- select a modern/pristine finish by default unless the chosen style is explicitly vintage
- use medium decoration density
- create only short, factually neutral copy
- avoid brands, pseudo-text, watermarks, and irrelevant stickers
- deliver one polished version

Do not ask a follow-up merely to learn preferred colors, stickers, typefaces, or photo position. Those are AI responsibilities in simple mode.

## Custom mode

Invite the user to supply only the fields they care about:

```text
照片：
主题或故事：
视觉风格：
字体气质／参考（可选）：
版式结构：
主图／必须使用的照片：
情绪与颜色：
装饰和材质：
新旧程度：现代干净／轻微手作／明确复古
摄影色调：自然／富士日系胶片／黑白纪实／其他
背景丰富度：轻／中／丰富
必须出现的准确文字：
照片处理限制：
装饰密度：
输出比例／用途：
AI自主程度：高／中／低
其他要求或禁用项：
```

Never require all fields. Fill blanks intelligently.

Interpret AI autonomy as:

- **High:** user fixes the story or one visual preference; AI resolves everything else.
- **Medium:** user fixes theme and layout or palette; AI resolves implementation details.
- **Low:** follow explicit specifications closely and add no unrequested narrative, copy, or motifs.

## When to ask

Ask only when one of these conditions applies:

- no understandable theme and visual inference would be arbitrary
- more than five photos compete for a single composition and mandatory photos are unclear
- a photo is too poor or obstructed to preserve the requested subject
- the user requests exact dates, names, locations, titles, or long copy without supplying them
- the user requests illustration or a transformation that may change a person's identity
- requirements conflict, such as “极简留白” and “每个空隙都放满贴纸”
- the requested layout requires a true calendar but the year, month, or week-start convention is missing

Ask a maximum of three short questions together. Recommend a default in the question when possible.

## Fact policy

### User or evidence must supply

- names and relationships
- dates, years, places, routes, and event names
- anniversaries and milestones
- titles, quotations, brands, and product facts
- chronological mapping for calendar layouts

### AI may invent safely

- titles such as “Slow Days” or “Weekend Notes”
- mood lines such as “把风收进口袋里”
- generic labels such as `FIELD NOTES`, `DAY LOG`, or `MEMORY 01`
- supporting graphics allowed by the selected visual style, such as labels, arrows, flat stickers, marker blocks, botanical marks, badges, or abstract shapes

Do not add tickets, stamps, tape, maps, dried plants, or torn paper automatically. They are style-specific options, not universal journal symbols.

Prefer cutout stickers made from the user's own photos—people, pets, food, vehicles, instruments, flowers, and meaningful objects—over generic stock stickers when the style permits. Do not force cutouts into minimal archive, full-bleed album, or other styles whose fingerprint prohibits them.

Do not invent a factual-looking location, timestamp, ticket number, brand, or relationship.

## Theme-derived association

Derive supporting motifs from all four signals:

`scene + activity + season + mood`

Examples:

- Mountain + summit + autumn + energetic: contour lines, route arrows, altitude badge, rust orange accent, rendered in the chosen style's graphic medium.
- Mountain + quiet stay + mist + reflective: sparse contour marks, window-light shapes, tea-cup motif, or quiet labels; use botanical specimens only when permitted by the selected style.
- Grass + picnic + spring + playful: gingham fragment, fruit, wildflower silhouettes, sunny yellow marks.
- City + night walk + rainy + cinematic: transit fragments, street-grid lines, reflective blue-black surfaces, restrained neon accent.

Never select motifs from the scene label alone.

## Default age policy

Default to **modern/pristine**, not vintage. Switch to aged surfaces only when:

- the user explicitly asks for vintage, retro, old diary, faded, nostalgic print, or similar aging; or
- the selected style family requires aging, specifically family 2 or family 6.

Words such as `安静`, `自然`, `日系`, `胶片`, `手绘`, `手帐`, `双页`, or `高密度` do not authorize yellowing, brown wash, torn kraft paper, stains, wrinkles, leather covers, or antique bindings.

When the user says `富士胶片`, `富士日系`, or equivalent, apply the photographic treatment defined from reference 4. Do not translate it into vintage page materials.

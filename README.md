# Make Photo Journal Art / 照片手帐生成器

把用户提供的照片与文字，制作成主题自适应的手帐、旅行日记、剪贴画、编辑杂志或电影感相册。

Turn user-supplied photos and stories into theme-adaptive journals, travel diaries, scrapbooks, editorial spreads, or cinematic albums.

## 能做什么 / What it does

- 根据照片内容提取色彩、光线、场景、人物和可抠图元素。  
  Extracts palette, lighting, setting, people, and cutout candidates from the supplied photos.
- 根据主题、地域、时代与情绪自动匹配版式、装饰和字体气质。  
  Adapts layout, decoration, and typography to the subject, place, period, and mood.
- 支持人物或物件抠图贴纸、照片边缘叠放、路线图、植物、票据和源照片衍生图形。  
  Supports source-derived person/object stickers, edge overlaps, route maps, plants, tickets, and abstract graphics.
- 默认保留人物身份和面部特征，不擅自改变衣着、人物或事实信息。  
  Preserves identity and facial features by default and does not invent clothing, people, or factual details.

## 如何使用 / How to use

上传一张或多张你有权使用的照片，然后选择简单模式或自定义模式。

Upload one or more photos you have the right to use, then choose either simple or custom mode.

### 简单模式 / Simple mode

只需提供主题或感觉，其余由 AI 决定。

Provide only a theme or feeling; AI decides the remaining art direction.

> 把这些照片做成“广西之行”的日系电影感手帐，安静、清新，其他由 AI 发挥。
>
> Turn these photos into a Japanese cinematic journal titled “A Journey Through Guangxi.” Keep it quiet and fresh; let AI decide the rest.

### 自定义模式 / Custom mode

可指定标题、主图、版式、色彩、情绪、装饰、照片处理、密度和 AI 自主程度；没有填写的项目由 AI 补全。

You may specify the title, lead photo, layout, palette, mood, decorations, photo treatment, density, and AI autonomy. AI fills in omitted fields.

```text
模式 / Mode: Crisp Japanese editorial magazine / 清爽日系编辑杂志
主题 / Theme: 十月山间旅行 / An October mountain journey
版式 / Layout: 高密度横版双页 / Dense landscape spread
主图 / Lead photo: 第4张 / Photo 4
文字 / Copy: 标题“云南之行”，短句由 AI 生成
              Title “A Journey Through Yunnan”; AI writes the short captions
照片处理 / Photo treatment: 允许裁切和抠图，不改变人物面部
                              Cropping and cutouts allowed; preserve faces
AI自主程度 / AI autonomy: 中 / Medium
```

## 风格中英对照 / Style glossary

| 中文 | English |
|---|---|
| 手工复古主题拼贴 | Handmade vintage thematic collage |
| 彩色手绘主题日记 | Colorful hand-drawn thematic diary |
| 富士胶片感日系电影相册 | Fujifilm-inspired Japanese cinematic album |
| 清爽日系编辑杂志 | Crisp Japanese editorial magazine |
| 路线地图备忘录信息图日记 | Route-map memo infographic diary |
| 光泽数字主题剪贴簿 | Glossy digital thematic scrapbook |

这些名称描述的是视觉语言，不要求复制任何特定作品。实际色彩、背景与元素会依据用户照片重新推导。

These names describe visual languages rather than requesting a copy of any specific artwork. Palette, background, and supporting elements are re-derived from the user's photos.

## 版权与隐私 / Copyright and privacy

- 本仓库不包含用于临摹的参考照片，也不依赖外部参考图运行。  
  This repository contains no reference photos for imitation and does not require external reference images.
- 生成只使用用户主动提供的照片、用户文字和原创的源照片衍生图形。  
  Generation uses only user-supplied photos, user-provided copy, and original source-derived graphics.
- 用户应确保拥有上传照片及文字的使用权，并避免要求复制特定在世艺术家的独特风格。  
  Users should have the right to use uploaded photos and text and should avoid requests to copy the distinctive style of a specific living artist.
- 若照片涉及他人、儿童、私密地点或敏感信息，请先获得适当授权并自行检查输出。  
  Obtain appropriate permission for photos involving other people, children, private locations, or sensitive information, and review outputs before sharing.

## Skill 结构 / Skill structure

```text
make-photo-journal-art/
├── SKILL.md
├── agents/openai.yaml
└── references/
    ├── input-modes.md
    ├── prompting-and-qa.md
    ├── style-families.md
    └── typography-routing.md
```

核心执行说明位于 `SKILL.md`；更细的输入模式、风格体系、提示词与字体路由规则按需从 `references/` 加载。

Core execution instructions live in `SKILL.md`. Detailed input modes, style systems, prompting guidance, QA, and typography routing are loaded from `references/` only when needed.

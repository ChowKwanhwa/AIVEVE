# Aivive Logo Prompts · 复古 80s 扫描线风 · v0.2

> 风格来源:`raw/logo/参考/star-1.avif`(横向扫描线填充的菱形星 + 几何 sans wordmark)+ `raw/logo/参考/relic-quartz.avif`(小圆 + 扫描线 + 颗粒噪点同心圆底)
> 品牌色板:Aqua `#4FFFD8`(primary)+ Coral `#FF8A5C`(accent)+ Ink `#08100E`(base)
> 品牌禁区:紫色、AI 彩虹渐变、neural network、circuit board、chip、cyberpunk
> 设计意图:借 80s 模拟电子/Synthwave 目录的 "pulse waveform + 温润噪点" 语言,与 Aivive 品牌 §10 Moodboard Motion 03 / Texture 02 同源

---

## 三个方向

- **A · Pulse Diamond** — 四角星/菱形由横向扫描线组成,中间最宽上下收窄(对标 star-1)
- **B · Warm Console** — 小实心圆 + 扫描线穿过圆 + 颗粒噪点同心圆底(对标 relic-quartz)
- **C · Scanline Monogram** — 字母 "a" 由横向扫描线堆叠构成,独立 icon 使用

---

## Midjourney v7 Prompts

> 通用修饰词:`--v 7 --style raw --ar 1:1`(或 `--ar 16:9` 做展示板)
> 必带品牌 sref:已挂 §10 Moodboard 到 `https://files.catbox.moe/7yba7e.png`(catbox 永久直链,MJ 可直接拉取);`--sw 400-600` 控制参考强度
> 不加 `--stylize` 默认(100),想更克制可降到 50

### A · Pulse Diamond(首选)

```
logo design for AI companion brand "Aivive", abstract four-pointed diamond star mark
composed of horizontal scanlines of varying width, narrow at top and bottom vertices
widening toward the horizontal center, subtle waveform rhythm, reminiscent of
1980s synthesizer panel graphics and Factory Records analog electronic aesthetic,
rendered in aqua #4FFFD8 with a thin coral #FF8A5C accent on the widest middle stripe,
isolated on deep teal-black #08100E background, clean geometric sans-serif wordmark
"aivive" lowercase placed to the right of the mark in the style of Favorit or Söhne,
monochrome precision, technical illustration feel, warm analog grain in background,
vintage trade catalog presentation
--ar 16:9 --v 7 --style raw --sref https://files.catbox.moe/7yba7e.png --sw 500
--no purple, violet, rainbow gradient, cyberpunk, neon, circuit, chip, brain, neural network, 3D, glossy, glassy highlight, emoji
```

### B · Warm Console

```
retro-futurist brand logo for "Aivive", small solid filled circle icon with five horizontal
scanlines passing through it like a CRT tube or a sun behind venetian blinds,
icon rendered in aqua #4FFFD8 with subtle coral #FF8A5C highlight on the topmost scanline,
stacked wordmark "Aivive" in clean geometric sans-serif (Söhne / Neue Haas Grotesk Display feel),
background is a warm analog grainy texture with faint concentric circles like sound ripples
on a dark teal-black #08100E field, 1986 synthesizer owner's manual aesthetic,
warm low-frequency noise, restrained monochrome palette with single coral accent,
album-cover feel, no gloss, no gradient, no depth
--ar 1:1 --v 7 --style raw --sref https://files.catbox.moe/7yba7e.png --sw 500
--no purple, violet, rainbow, cyberpunk, neon, circuit, chip, neural, 3D render, glossy, AI art
```

### C · Scanline Monogram(辅标/icon-only 用)

```
minimal app icon mark, letterform "a" lowercase constructed entirely from stacked horizontal
scanlines of varying width, narrow lines at top and bottom, widest line through the middle
crossbar, clean geometric construction, aqua #4FFFD8 stripes on deep teal-black #08100E,
one single coral #FF8A5C stripe at the exact vertical center for rhythm,
1980s industrial catalog aesthetic, technical schematic precision, analog grain texture,
monochrome restraint, vector-ready flat construction, no highlights, no shadow, no bevel
--ar 1:1 --v 7 --style raw --sref https://files.catbox.moe/7yba7e.png --sw 600
--no purple, violet, rainbow, neon glow, 3D, bevel, glossy, skeuomorphic, emoji, circuit, brain, neural
```

### 跑图节奏建议

1. 每个方向先跑 `--sref random` 的版本 + 指定 `https://files.catbox.moe/7yba7e.png` 的版本,各 8-12 张,看哪个"锚点"更稳
2. 挑 2-3 张喜欢的 → 点 `Vary (Subtle)` 做 4 张微调
3. 再用 `/blend` 把 A 和 B 融合,可能出意外的最优解
4. 最终选 5 张送给设计师做 **矢量化 + 调字距**(AI 出的字标不能直接交付)

---

## Nano Banana Pro Prompts(字标精准 & 干净底色用 NBP)

> NBP 的强项:英文字 **精准到字形**、`#hex` 色值几乎一次命中、底色干净、可对话迭代
> 使用方式:直接粘进 Gemini app(免费额度)或 AI Studio
> 迭代技巧:出图后直接说 "make the coral stripe thinner / move the mark closer to the wordmark / increase grain intensity" 即可

### A · Pulse Diamond · 交付级字标

```
Create a minimal horizontal logo lockup for an AI brand called "Aivive".

ICON (left side):
- An abstract four-pointed diamond star mark composed entirely of 9 horizontal scanline
  stripes of varying widths
- Stripe width pattern from top to bottom: 2px, 3px, 5px, 8px, 12px (widest, center),
  8px, 5px, 3px, 2px — creates a diamond silhouette
- Stripes are horizontal only, never angled
- Fill color: aqua #4FFFD8
- The single widest center stripe: a subtle gradient from aqua #4FFFD8 to coral #FF8A5C
- Total icon width roughly 20% of canvas

WORDMARK (right side, centered vertically with icon):
- The word "aivive" in lowercase
- Font: a clean geometric sans-serif in the spirit of Favorit or Söhne, Light weight
- Color: pure white #FFFFFF
- Spacing between icon and wordmark: equal to the x-height of the wordmark

BACKGROUND:
- Deep teal-black #08100E solid, no texture, no grain
- 16:9 aspect ratio
- Very generous padding around the entire lockup (at least 40% of canvas is empty)

STYLE REFERENCE:
Think 1980s Factory Records album credits, Sony synthesizer owner manual covers,
early Macintosh retail packaging — precise, monochrome, warm-tech, not cyberpunk,
not AI-art, not glossy. Flat vector feel.

OUTPUT: 2K resolution, 16:9
```

### B · Warm Console · 有噪点底

```
Design a square brand lockup for "Aivive" inspired by 1980s electronic music album art.

ICON (centered above wordmark):
- A small solid filled circle, 80px diameter on a 1200px canvas
- 5 horizontal stripes of equal spacing cutting across the circle, subtracting from the fill
- Circle color: aqua #4FFFD8
- Topmost stripe: thin coral #FF8A5C line just above the circle, suggesting a horizon

WORDMARK (below icon, stacked two lines, centered):
- Line 1: "Aivive" in Title Case
- Line 2: "The AI that gives." in smaller weight
- Font: clean geometric sans-serif, Medium weight for line 1, Regular for line 2
- Color: pure white #FFFFFF

BACKGROUND:
- Deep teal-black #08100E base
- Overlay: warm analog film grain at 8% opacity
- Overlay: 6 faint concentric circles emanating from the icon position, like sound ripples,
  at 5% opacity, aqua #4FFFD8 hue
- Square 1:1 aspect ratio

MOOD:
1986 synthwave album sleeve, Tangerine Dream gatefold, warm low-frequency noise,
restrained monochrome, NOT cyberpunk, NOT neon, NOT purple, NOT 3D.

OUTPUT: 2K resolution, 1:1 square
```

### C · Scanline Monogram · 纯 icon 尺寸应用

```
Create a single app icon mark, no text, no tagline.

SUBJECT:
- The lowercase letter "a" constructed entirely from stacked horizontal scanlines
- 11 horizontal stripes total, varying widths to form a recognizable "a" shape:
  a tall closed counter on top and a small open bowl on the bottom
- All stripes are purely horizontal — the letter's curves are suggested only by stripe length
- Stripe color: aqua #4FFFD8
- One single stripe at the exact vertical middle: coral #FF8A5C
- No outline, no stroke, no shadow, no highlight, no gradient beyond the single coral accent

BACKGROUND:
- Deep teal-black #08100E solid fill
- Canvas: 1024x1024 square
- Icon occupies ~60% of canvas, perfectly centered
- Safe margin on all sides equal to 20% of canvas width

STYLE:
1980s industrial parts catalog, technical schematic, vector-flat, monochrome restraint,
NOT AI-art, NOT glossy, NOT 3D, NOT bevel, NOT skeuomorphic. Favorit-grotesque DNA.

OUTPUT: 2K resolution, 1:1 square
```

---

## 出图后的筛选标准

打分表(每项 1–5):

| 维度 | 评价问题 |
|---|---|
| 扫描线是否纯横向 | 只要有任何斜线/曲线就 -2 分 |
| Aqua 是否准确 | 偏青偏绿都不对,目标 #4FFFD8 |
| Coral 是否收敛 | 只该在 1-2 根线上出现,不能铺成渐变 |
| 是否去除 AI 味 | 任何光晕/发光/3D 厚度/赛博朋克霓虹都 -3 分 |
| 字标是否工整 | 字重、字距、字形干净 → ≥4 分才算可用 |
| 给设计师矢量化难度 | 看图一眼能想象用 Figma 矩形 + rect 画出来 → 5 分 |

**5 分 × 5 项 = 25 分门槛,≥20 分的 5 张** 进入阶段 2(交给设计师)。

---

## 下一步

1. 跑图:按 `MJ A → NBP A → MJ B → NBP B → MJ C → NBP C` 顺序各 20 张
2. 按打分表挑 3-5 张最终候选,拼成 Figma 概念板
3. 带上 Brand Brief 文件链接(`figma.com/design/zUkPA30Kxd2pI2Tq143yAo`)+ 这 5 张候选 + `wiki/design/aivive-design.md` 给设计师
4. 和设计师对齐后,产出矢量 SVG + 字距微调 + 各尺寸导出

**重申**:AI 输出的任何一张都 **不是** 最终 logo,只是概念板。最终交付必须是设计师的矢量稿。

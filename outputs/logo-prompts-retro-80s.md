# Aivive Logo Prompts · 复古 80s 扫描线风 · v0.3(纯 icon,无文字)

> 风格来源:`raw/logo/参考/star-1-iconly.png`(横向扫描线填充的菱形星,已去水印)。原 `relic-quartz` 构图带文字,已从参考池剔除。
> 品牌色板:Aqua `#4FFFD8`(primary)+ Coral `#FF8A5C`(accent)+ Ink `#08100E`(base)
> 品牌禁区:紫色、AI 彩虹渐变、neural network、circuit board、chip、cyberpunk
> 设计意图:借 80s 模拟电子/Synthwave 目录的 "pulse waveform + 温润噪点" 语言,与 Aivive 品牌 §10 Moodboard Motion 03 / Texture 02 同源
> **本版全部为 mark-only**:不生成任何文字、wordmark、tagline、label、字母 — 后续字标由设计师用 Söhne/Favorit 单独排版

---

## 三个方向(全部纯 icon)

- **A · Pulse Diamond** — 四角星/菱形由横向扫描线组成,中间最宽上下收窄(对标 star-1)
- **B · Warm Console** — 小实心圆 + 横向扫描线穿过 + 颗粒噪点同心圆底(对标 relic-quartz)
- **C · Pulse Sigil** — 纯抽象横向条纹堆叠 sigil,像 equalizer / pulse waveform 的定格,无字母含义

---

## Midjourney v7 Prompts

> **策略**:v0.3.3 起用 **image prompt**(把参考图 URL 直接放 prompt 最前面)而不是 `--sref`。image prompt 影响构图 + 风格 + 调性,比 sref 严格得多,适合复现 `star-1-iconly.png` 这种**密集细横线 + 印刷感**的精确几何。参考图已裁干净,去掉原图里的 "Star-1™" 文字以防 MJ 把文字也抄进 logo。
> ⚠️ **MJ image prompt 只支持 PNG / JPG / WebP,不吃 AVIF**。本地 `raw/logo/参考/*.avif` 先用 `sips -s format png x.avif --out x.png` 转 PNG 再上传,否则 MJ 会静默忽略 image prompt。
> **关键参考图**(image prompt):`https://litter.catbox.moe/okzgd9.png` — star-1 的**裁干净版本**(`raw/logo/参考/star-1-iconly.png`),已去掉原图右侧 "Star-1™" 文字,只保留菱形本身。litterbox 链接 72h 过期,失效后让我重传即可。
> **参数**:`--iw 2`(image weight 拉满,逼 MJ 贴着参考画)+ `--s 25`(stylize 极低,减少 MJ 自由发挥)+ `--style raw` + `--v 7`
> **不再用 moodboard sref**:避免和 image prompt 的风格指令打架

### A · Pulse Diamond(首选 — 直接对标 star-1)

```
https://litter.catbox.moe/okzgd9.png flat logo mark, diamond made of dense thin horizontal parallel lines, aqua #4FFFD8 lines on dark teal-black #08100E background, one single coral #FF8A5C line in the exact middle, engraved print aesthetic, risograph, letterpress, flat 2D vector, minimalism, centered icon
--ar 1:1 --v 7 --style raw --s 25 --iw 2
--no text, letters, words, typography, wordmark, logo text, lettering, inscription, glow, neon, 3D, gradient, shadow, glossy, highlight, mountains, landscape, album cover, scene, photography, perspective, depth, purple, violet, rainbow, cyberpunk, circuit, chip, brain, neural, emoji
```

### B · Warm Console(圆 + 扫描线,对标 relic-quartz)

> **参考图改用 star-1-iconly**(只做风格锚,不做构图锚)。原 `relic-quartz.png` 带 "Relic Quartz" 文字污染,不适合做 image prompt。B 构图(小圆+5横线)跟 star-1 的菱形不一样,所以把 `--iw` 降到 `1`,让 MJ 参考调性但不抄构图。

```
https://litter.catbox.moe/okzgd9.png flat logo mark, a small solid filled aqua #4FFFD8 circle with 5 thin horizontal lines cutting through it evenly spaced, one coral #FF8A5C line just above the circle suggesting a horizon, dark teal-black #08100E background with very faint concentric circles at low opacity like sound ripples, subtle warm analog grain, flat 2D vector, engraved print aesthetic, risograph, centered icon
--ar 1:1 --v 7 --style raw --s 25 --iw 1
--no text, letters, words, typography, wordmark, logo text, lettering, inscription, glow, neon, 3D, gradient, shadow, glossy, highlight, mountains, landscape, album cover illustration, scene, photography, perspective, purple, violet, rainbow, cyberpunk, circuit, chip, brain, neural, emoji
```

### C · Pulse Sigil(纯几何 sigil,用 star-1 做风格锚)

```
https://litter.catbox.moe/okzgd9.png flat logo mark, stack of dense thin horizontal parallel lines forming a symmetric sigil, narrow lines at top and bottom progressively widening to the middle where the longest line sits, aqua #4FFFD8 lines on dark teal-black #08100E, one coral #FF8A5C line in the exact vertical center, engraved print aesthetic, risograph, letterpress, flat 2D vector, geometric abstraction only, centered icon
--ar 1:1 --v 7 --style raw --s 25 --iw 1.5
--no text, letters, words, alphabet, typography, wordmark, lettering, inscription, monogram, glow, neon, 3D, bevel, gradient, shadow, glossy, mountains, landscape, scene, album cover, photography, purple, violet, rainbow, cyberpunk, circuit, chip, brain, neural
```

> C 用 `--iw 1.5` 而非 2:C 是"抽象对称条纹"不是菱形,稍微松一点让 MJ 能变通出非菱形轮廓。

### 跑图节奏建议

1. **先跑 A 和 C 各 4 张**(都用 star-1 image prompt),看 image prompt + `--iw 2/1.5` 是否真的让风格贴近参考
2. 如果 A 出来的菱形还是太"logo badge 感"、带发光/3D:把 `--iw 2` 拉到 `--iw 3`(image prompt 权重最大为 3),同时 `--s` 降到 `10`
3. 如果反过来,想让 MJ 更发挥一点不要死贴参考:`--iw 1`
4. B 跑 4 张,用 star-1-iconly 作风格锚 `--iw 1`。如果 MJ 把 B 也画成菱形(被参考图构图带偏),把 `--iw` 去掉让 MJ 纯文本生成
5. 挑到喜欢的 → `Vary (Subtle)` 做 4 张微调
6. 终选 5 张送设计师做 **矢量化 + 单独配字标**

> ⚠️ **参考图 URL 72h 过期**(`litter.catbox.moe` 临时链接)。过期后 image prompt 会静默失败(MJ 拉不到图,等于没传 image prompt,prompt 还能跑但不会贴参考)。让我重新上传 `raw/logo/参考/star-1-iconly.png` 拿新 URL 即可。

---

## Nano Banana Pro Prompts(干净底色 + 精准 hex 用 NBP)

> NBP 的强项:`#hex` 色值几乎一次命中、底色干净、可对话迭代
> 使用方式:直接粘进 Gemini app(免费额度)或 AI Studio
> 迭代技巧:出图后直接说 "make the coral stripe thinner / reduce grain intensity / center the mark" 即可
> 本版 **全部不含任何文字/字母/字标**,最终字标由设计师单独排

### A · Pulse Diamond · 纯 icon 版

```
Create a minimal centered icon mark. NO TEXT, NO LETTERS, NO WORDMARK, NO TAGLINE
anywhere in the image.

ICON:
- An abstract four-pointed diamond star mark composed entirely of 9 horizontal scanline
  stripes of varying widths
- Stripe width pattern from top to bottom: 2px, 3px, 5px, 8px, 12px (widest, center),
  8px, 5px, 3px, 2px — creates a diamond silhouette
- Stripes are horizontal only, never angled
- Fill color: aqua #4FFFD8
- The single widest center stripe: a subtle gradient from aqua #4FFFD8 to coral #FF8A5C
- Icon occupies roughly 40% of the canvas, perfectly centered

BACKGROUND:
- Deep teal-black #08100E solid, no texture, no grain
- Square 1:1 aspect ratio
- Very generous padding on all sides (safe margin ~30% of canvas width)

STYLE REFERENCE:
Think 1980s Factory Records album credits, Sony synthesizer owner manual covers,
early Macintosh retail packaging — precise, monochrome, warm-tech, not cyberpunk,
not AI-art, not glossy. Flat vector feel.

STRICT: Do NOT render any letters, words, numbers, or typography. Pure icon only.

OUTPUT: 2K resolution, 1:1 square
```

### B · Warm Console · 有噪点底

```
Design a square icon mark inspired by 1980s electronic music album art.
NO TEXT, NO LETTERS, NO WORDMARK, NO TAGLINE anywhere in the image.

ICON (centered):
- A small solid filled circle, 200px diameter on a 1200px canvas
- 5 horizontal stripes of equal spacing cutting across the circle, subtracting from the fill
- Circle color: aqua #4FFFD8
- Topmost stripe: thin coral #FF8A5C line just above the circle, suggesting a horizon

BACKGROUND:
- Deep teal-black #08100E base
- Overlay: warm analog film grain at 8% opacity
- Overlay: 6 faint concentric circles emanating from the icon position, like sound ripples,
  at 5% opacity, aqua #4FFFD8 hue
- Square 1:1 aspect ratio

MOOD:
1986 synthwave album sleeve, Tangerine Dream gatefold, warm low-frequency noise,
restrained monochrome, NOT cyberpunk, NOT neon, NOT purple, NOT 3D.

STRICT: Do NOT render any letters, words, numbers, captions, or typography.
This is a pure icon composition, no wordmark, no tagline.

OUTPUT: 2K resolution, 1:1 square
```

### C · Pulse Sigil · 纯抽象 sigil

```
Create a single abstract pulse sigil mark. NO TEXT, NO LETTERS, NO ALPHABET,
NO MONOGRAM, NO WORDMARK, NO TAGLINE anywhere in the image.

SUBJECT:
- Stack of 11 horizontal stripes forming a symmetric abstract sigil
- Stripe widths (top to bottom, in px on 1024 canvas):
  40, 80, 160, 240, 320, 400 (widest, center), 320, 240, 160, 80, 40
- Equal vertical spacing between stripes (about 16px)
- All stripes are purely horizontal — this is pure geometric abstraction, not a letter
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

STRICT: This composition must NOT contain any letters (including "a", "A", or any other
character), numbers, words, typography, or text of any kind. Pure geometric sigil only.

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
| **是否纯 icon(无文字)** | 出现任何字母/单词/标点 → **直接 0 分** |
| 给设计师矢量化难度 | 看图一眼能想象用 Figma 矩形 + rect 画出来 → 5 分 |

**5 分 × 5 项 + 1 项 0/5 硬门槛 = 25 分上限**,≥20 分且无文字出现的 5 张进入阶段 2(交给设计师配字标)。

---

## 下一步

1. 跑图:按 `MJ A → NBP A → MJ B → NBP B → MJ C → NBP C` 顺序各 20 张
2. 按打分表挑 3-5 张最终候选(有文字的一律作废),拼成 Figma 概念板
3. 带上 Brand Brief 文件链接(`figma.com/design/zUkPA30Kxd2pI2Tq143yAo`)+ 这 5 张候选 + `wiki/design/aivive-design.md` 给设计师
4. 设计师用 Söhne / Favorit 手排字标(`aivive` lowercase,Light 字重),与 icon 组成 lockup,产出矢量 SVG + 各尺寸导出

**重申**:AI 只出 **mark**,**字标必须由设计师单独排** — 这是本版 prompt 全部去文字的根本原因。AI 的英文字标字距、连字、底部圆弧都不达交付级。

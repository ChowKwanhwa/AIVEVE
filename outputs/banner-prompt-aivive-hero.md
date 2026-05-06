---
title: AIVIVE Hero Banner Prompt (nbp / Nano Banana Pro)
type: prompt
status: draft
tags: [aivive, banner, nbp, marketing]
sources:
  - raw/参考/TermiX-hero-banner.jpeg
  - raw/logo/正式logo/wordsBelow2.png
  - wiki/design/aivive-design.md
updated: 2026-04-22
---

# AIVIVE Hero Banner — nbp Prompt

> **用法**:在 Nano Banana Pro 里同时上传两张参考图:
> - **Ref 1** = TermiX 海报原图(构图锚)
> - **Ref 2** = AIVIVE 官方 logo(品牌锚,`raw/logo/正式logo/wordsBelow2.png`)
>
> 然后粘贴下方 prompt。一次跑 4 张,挑最接近的再微调 headline。

---

## Prompt(直接复制)

```
Re-skin the TermiX hero banner (Ref 1) to AIVIVE brand using the AIVIVE logo lockup (Ref 2).
Keep the overall composition intact: 1280x672 horizontal banner, left 55% is title stack,
right 45% is a 3D hero object, logo sits top-left corner, subtle grid + stars on background.

Replace ALL TermiX visual content as follows:

LOGO LOCKUP (top-left):
Use Ref 2 exactly — the AIV curved monogram with an aqua-to-coral gradient diamond star
in the middle, "AIVIVE" wordmark stacked below, on transparent.
Size: ~160px tall, 48px from top-left corner.

COLOR SYSTEM (hard rules):
- neon green #B8FF30 → aqua #4FFFD8
- pure black → ink #0B0720 (deep violet-black, not pure black)
- white for primary text (unchanged)
- add coral #FF8A5C as secondary warm accent only where a reward/CTA would go
- soft violet #5B3BEE allowed inside the 3D hero object's gradient, nowhere else

HEADLINE (left side, replacing "STANDARDIZING THE AGENT ECONOMY"):
Line 1: "KEEP AI" in bold white sans-serif, 72pt, weight 800, letter-spacing -0.02em
Line 2: "ALIVE." in italic serif (Instrument Serif feel), 72pt, filled with aqua→coral
linear gradient (135deg, #4FFFD8 0%, #FF8A5C 100%)

SUBTITLE (below headline, replacing the ERC line):
"AI + social on Solana. Open, owned, community-first."
18pt, regular weight, color #C6BDE1 (muted lavender-white)

3D HERO OBJECT (right side, replacing the white robotic machine):
Cluster of 3-5 floating glass-morphism orbs, semi-translucent, isometric perspective.
Inner gradient flow: aqua #4FFFD8 → violet #5B3BEE → coral #FF8A5C.
Each orb has a soft outer halo glow (aqua-tinted, 40px blur).
Scatter 2-3 floating diamond-star coin tokens matching the AIVIVE logo's star shape,
in aqua-coral gradient, tilted at isometric angles.
Breathing / alive quality — looks like it's pulsing, not mechanical.
NO robots. NO circuit boards. NO machine parts. NO gears.

BACKGROUND:
Base fill: ink #0B0720 deep violet-black.
Left edge: soft aqua radial glow (#4FFFD8 at 25% opacity, large radius) radiating
from behind the logo corner — mirrors TermiX's green glow but in aqua.
Grid lines: same density as TermiX original, re-tinted to aqua #4FFFD8 at 8% opacity.
Scattered tiny stars: white and aqua, 1-2px, low density, organic distribution.
2-3 faint orb trail streaks in the mid-back, suggesting motion/flow.

STYLE NOTES:
- Alive, warm, sharp — not corporate, not meme, not generic crypto
- Keep the isometric 3D render style from Ref 1 (it's good)
- Keep the typographic hierarchy from Ref 1 (headline / sub / logo all in same positions)
- Treat this as a real product launch banner, not a concept art piece

DO NOT:
- No horse imagery of any kind
- No red, no yellow, no corporate blue
- No flat vector illustration, no line art
- No spinning wheels, no loading spinners
- No text on the hero object itself
- No extra wordmarks besides the one in the logo lockup

Output: 1280x672, PNG with no compression artifacts, crisp edges.
```

---

## Variants(如果要跑多个 headline)

保留 prompt 其它部分不变,只替换 headline 部分:

### V1 — Keep AI Alive(默认,推荐)
```
Line 1: KEEP AI   (bold white sans)
Line 2: ALIVE.    (italic serif, aqua→coral gradient)
```

### V2 — The AI That Gives
```
Line 1: THE AI THAT   (bold white sans)
Line 2: GIVES.        (italic serif, aqua→coral gradient)
```

### V3 — Come In, Stay a While
```
Line 1: COME IN.      (bold white sans)
Line 2: STAY A WHILE. (italic serif, aqua→coral gradient, smaller 56pt)
```

### V4 — Subtle(无渐变,纯白)
```
Line 1: KEEP AI       (bold white sans)
Line 2: alive.        (italic serif lowercase, aqua solid #4FFFD8)
```

---

## 跑图后的筛选清单

拿到 4 张候选后按这个顺序刷:

1. **Logo 清晰度**:左上角 AIVIVE 菱形星星是否糊掉/变形 —— nbp 经常把渐变小元素糊成噪点,糊了就弃
2. **色准**:aqua 是否偏绿(变成 TermiX 那种 `#B8FF30`)—— 如果偏绿,prompt 里加 "aqua #4FFFD8 is cyan-tinted, NOT lime green"
3. **背景深度**:是否变成纯黑 `#000`(太硬)—— 如果是,prompt 里 `#0B0720` 改成 `#0B0720 deep violet-black, never pure black, warmth of indigo`
4. **3D 物体**:有没有混进机器人/电路板(nbp 见到"crypto"默认会加这些)—— 看到就删版本重跑,强化禁区那段

---

## 为什么这样写

- **双 ref 图策略**:Ref 1 管构图,Ref 2 管品牌身份。只给 Ref 1 会跑出 TermiX 山寨,只给 Ref 2 会跑出 logo 单图而非 banner。
- **Hard rules 色替换**:显式告诉模型"X 换成 Y",比让它自行理解 AIVIVE 色系稳。
- **3D hero 重写**:TermiX 的机器装置是品牌核心视觉资产,AIVIVE 的核心视觉是"呼吸的生命体",必须整块替换,不能只换颜色。
- **DO NOT 列表**:AIVIVE 设计系统 §2.7 + §7.2 的禁区,nbp 经常脑补,这些不压住就失控。

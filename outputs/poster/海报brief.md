# Aivive 海报 Brief · V1 Mystery Phase

> **给设计师**:5 张海报,V1 神秘期使用。出图前请通读 §0 品牌约束,**任何违反硬约束的稿一律重做**。
> **完整品牌系统**:`wiki/design/aivive-design.md`(单一事实源)
> **附件配色**:`/Users/ericc/Desktop/土豆/aiavive-app/lib/design/tokens.ts`(代码侧 token,可对照)

---

## 0. 品牌硬约束(每张海报必须遵守)

### 颜色 — v0.2 系统

```
✅ 允许使用:

aqua (主色, 对应 "Vive" — 生命/活力):
  aqua-200  #A8FFEB
  aqua-300  #7BFFE3
  aqua-400  #5DFFDC
  aqua-500  #4FFFD8   ← PRIMARY 锚点
  aqua-600  #1FE8BC
  aqua-700  #0E9E80
  aqua-800  #0B7A63
  aqua-900  #08584A

coral (暖锚, 对应 "Give" — 温度/给予):
  coral-100 #FFE0D0
  coral-300 #FFBC9D
  coral-400 #FFA37D
  coral-500 #FF8A5C   ← ACCENT 锚点
  coral-700 #C9572E
  coral-900 #7A2F11

ink (中性, teal-black hue 160°):
  ink-0    #FFFFFF
  ink-50   #ECF7F2
  ink-100  #D5EBE2
  ink-300  #84B0A2   ← 深色底主文本
  ink-500  #4A6E62   ← 深色底次级文本
  ink-700  #1F3D34   ← 深色 muted 表面
  ink-800  #16302A   ← 深色 raised 表面
  ink-900  #0E2520   ← 深色 panel 底
  ink-950  #08100E   ← 深色 base 背景(默认)

✅ 渐变(只准 2-stop, 不准 3-stop):
  brand:      aqua-500 → coral-500       (135°)
  brand-soft: aqua-300 → coral-300       (135°)
  radial:     aqua-500 透明度 → 透明     (用作发光 vignette)

❌ 完全禁止:
  ❌ 任何紫色 / violet / purple
  ❌ 任何红色 / red(error 用 coral-700, 不用红)
  ❌ 3-stop 渐变(violet→coral→aqua 已退役)
  ❌ 纯黑 #000(用 ink-950 #08100E 替代)
  ❌ 真人 / 人脸 / 政治符号 / 儿童形象(KuCoin 上所合规红线)
  ❌ 马 / 马蹄 / 任何 Red Horse 相关意象(已切断品牌血缘)
  ❌ AI 套路图(机器人 / 电路板 / 大脑齿轮 / 紫色 orb)
```

### 字体

```
Sans 默认:    Geist Sans          (大部分文字)
Mono:        Geist Mono          (代码 / 技术示意)
Display 衬线: IBM Plex Serif      (★ 仅用于关键词强调)

衬线使用规则(★ 严格):
  - 仅当出现 Aivive / Give / Vive 这三个词作为单词级强调时
  - 用 italic + 较其余文字大 1-2 档
  - 配合 brand-gradient text-fill 效果尤佳
  - 其他场景一律 sans
```

### 调性(必须传达)

```
Alive    — 有呼吸感、有脉冲、有光。不死寂、不静态
Warm     — 有人味、能分享。不企业、不冷峻
Sharp    — 结构清晰、信息密度高。不松散、不 meme
```

### Signature motion(可静态海报上暗示)

```
Breathe 2.8s — logo / orb 轻微缩放 1.0 → 1.015 → 1.0,同时 aqua glow
              半径波动。承载 "AI is alive" 叙事。海报里用 1-2 个柔和
              ring 包围 orb 暗示这个动效。
```

---

## 1. Poster M1 — "Soon" / Mystery Hero(★ 优先出)

### 用途

- Twitter pinned tweet 配图
- Telegram channel 顶图
- Linktree 顶图
- 着陆页首屏背板(可选)

### 文案

```
Headline:    Soon.

Body:        Aivive
             alive · warm · sharp

Footer:      aivive.ai · @AIVIVEHQ
```

### 视觉规范

- **中央**:一个 aqua → coral 渐变 orb(135° gradient,直径占画面 30-40%)
- **Breathe 暗示**:orb 外围 2 个柔和 ring(透明度 15% / 8%,半径递增)
- **"Soon"**:IBM Plex Serif italic,极大字号(占画面纵向 1/4),颜色用 brand-gradient text-fill
- **Aivive**:sans semibold,中等字号,ink-100
- **alive · warm · sharp**:极小字号横排,coral-500 中点 `·` 分隔,ink-300
- **Footer**:极小字号,ink-500
- **背景**:ink-950 (#08100E),整体大量留白(orb 周围至少留 20% 空白)

### 输出比例

```
1080×1080  Twitter 主图 / Instagram post
1080×1920  Twitter Story / Instagram Story / Reels 封面
```

### 给设计师的注意

```
- 不要把 orb 做成"机器人头" / "脑子" / "齿轮" — 就是一个柔和发光的渐变球
- "Soon" 字号一定要大,大到几乎要溢出画面,这是视觉 punchline
- 整张图的"留白比例"比"内容比例"更重要 — 神秘感来自留白
```

---

## 2. Poster M2 — "The Loop" / 哲学诗意

### 用途

- 推文 B2(`the alive ones come back to the loop ↻`)配图
- 周末发推,KOL 转发友好

### 文案

```
Headline:    The alive ones
             come back
             to the loop.

Subhead:     ↻

Body:        (无)

Footer:      Aivive · soon
```

### 视觉规范

- **中央**:一个无限符号 / mobius 环 / 圆环 形状,aqua → coral 2-stop 渐变描边(stroke 1.5px,匹配 lucide icon stroke)
- **形状选择**:倾向用真正的 mobius 环(立体扭转),不是简单的圆 — 暗示"alive 的循环"
- **三行文案**:垂直居中,字号 4xl-5xl,ink-100,sans semibold
- **↻ 符号**:单独一行,稍小,coral-500
- **背景**:ink-950
- **可选**:微弱的 coral 粒子从环上"飞"出再"回来",暗示循环

### 输出比例

```
1080×1080  square (Twitter / IG / TG 通用)
```

### 给设计师的注意

```
- mobius 环要画得"alive" — 线条粗细可以微变化,不是均匀机械的
- 三行文字之间的行距可以略大(1.4-1.5),让"come back to the loop" 有节奏感
```

---

## 3. Poster M3 — "Three Words" / 品牌人格

### 用途

- 推文 C2(`never use purple`)配图
- KOL repost-bait(无信息密度,纯调性)
- Twitter banner(1500×500 横版)

### 文案

```
Headline:    Alive.
             Warm.
             Sharp.

Subhead:     What kind of AI
             do you want to live with?

Body:        (无)

Footer:      aivive.ai
```

### 视觉规范

- **三词**:竖排,极大字号(display, 7xl-9xl,占画面纵向 60%+)
  - **"Alive."**:aqua glow 描边 + 实心 ink-100 fill
  - **"Warm."**:coral glow 描边 + 实心 ink-100 fill
  - **"Sharp."**:仅 ink-100 实心(不发光,对比前两词的"冷峻锐利")
- **Subhead**:衬线 italic(IBM Plex Serif),居中,ink-300,字号 lg-xl
- **三词之间**:微小的呼吸 orb(aqua-500,直径占字号 1/8,极小)作为视觉 anchor
- **背景**:ink-950
- **Footer**:极小,ink-500,底部居中

### 输出比例(★ 出 2 个)

```
1080×1080  Twitter / IG 主图
1500×500   Twitter banner(三词改横排,Subhead 在三词下方)
```

### 给设计师的注意

```
- 三词的句号 "." 是重点 — 给品牌定调时是"声明",不是"形容"
- "Sharp." 没有 glow 是关键设计意图:让对比凸显
- banner 版本可以把 "Alive · Warm · Sharp" 横排 + 中点分隔,但句号保留
```

---

## 4. Poster M4 — "Harness eats the model" / 教学帖配图

### 用途

- 推文 A1(`the harness eats the model`)+ Thread T1 第 1 条 配图
- 显示 AI 工程深度,吸 builder 圈

### 文案

```
Headline:    The harness
             eats
             the model.

Body:        Same model.
             Different scaffolding.
             Different outputs.

             You're not using AI.
             You're using a harness around AI.

Footer:      Aivive · aivive.ai
```

### 视觉规范

- **中央**:一个 model 抽象球体(aqua glow,半透明实心,直径占画面 25%)
- **外围**:一层几何 harness 骨架(ink-300 线条 + 节点,非具象)— 想象成"线框监狱"或"骨骼外架"包住 orb
- **张力**:harness 应该看起来"about to eat / consume" orb — 节点稍微逼近 orb 表面,可有微小的"接触"光晕
- **"eats"**:IBM Plex Serif italic,brand-gradient text-fill,作为视觉重点
- **Headline**:左对齐,3 行排版,大字号
- **Body**:Headline 下方,中字号,ink-300,行距宽
- **背景**:ink-950
- **Footer**:小字号,ink-500

### 输出比例

```
1200×675   Twitter 卡片(横版,主用)
1080×1080  Twitter / IG 主图(竖版备选)
```

### 给设计师的注意

```
- harness 骨架是"几何 wireframe",不是真的笼子 — 类似 Three.js wireframe 风格
- orb 不是机器人脑袋,就是一个发光的渐变球
- "eats" 这个词的视觉位置可以稍微偏离行的基准线,有"动感"
```

---

## 5. Poster M5 — Day Counter / 长期序列

### 用途

- 每周更新一张,体现节奏 + 制造"在跑"信号
- 推文 P2F1 / E1 / build-in-public 类配图
- 这是 **template** — 你出一版,我们后续每周改 day 数 + 进度条位置

### 文案

```
Headline:    Day [N] of 60.

Subhead:     We're cooking.

Body:        ━━━━●━━━━━━━━━━━━━━

Footer:      @AIVIVEHQ
```

### 视觉规范

- **进度条**:横向贯穿画面,占宽度 80%,垂直居中略偏下
  - 已过去的 day:aqua-700 实心 line
  - 当前 day:coral-500 实心圆 + glow halo(直径是 line 高度的 4x)
  - 未来 day:ink-700 空心(虚线或淡色 line)
- **Headline**:进度条上方,大字号(5xl-7xl),sans semibold,ink-100
  - "Day" sans
  - "[N]" brand-gradient text-fill, 略大字号
  - "of 60" sans, ink-300
- **Subhead**:Headline 下方,衬线 italic,ink-300,中字号
- **背景**:ink-950
- **Footer**:右下角,小字号,ink-500

### 输出比例

```
1080×1080  square(Twitter / IG / TG 通用)
```

### 给设计师的注意

```
- 这是 template,出一版 PSD/Sketch/Figma 源文件,以后我们改 [N] 数字 + 移动 ● 位置即可
- coral 当前点的 glow 不要太亮,保持克制(这是周更图,不能每周都"炸")
- 进度条样式可以参考 Vercel / Linear 的 build progress 视觉
```

---

## 6. 输出 / 交付清单

每张海报请按下表交付:

| Poster | 必交付 | 可选 |
|---|---|---|
| M1 Soon Hero | 1080×1080 + 1080×1920 PNG/JPG | Figma / PSD 源 |
| M2 The Loop | 1080×1080 PNG/JPG | mp4 短动画(可选) |
| M3 Three Words | 1080×1080 + 1500×500 PNG/JPG | Figma 源 |
| M4 Harness | 1200×675 + 1080×1080 PNG/JPG | Figma 源 |
| M5 Day Counter | 1080×1080 PNG/JPG + **template 源文件**(★ 必给)| — |

文件命名:

```
aivive-poster-M1-soon-hero-1080x1080.png
aivive-poster-M1-soon-hero-1080x1920.png
aivive-poster-M2-loop-1080x1080.png
aivive-poster-M3-three-words-1080x1080.png
aivive-poster-M3-three-words-1500x500.png
aivive-poster-M4-harness-1200x675.png
aivive-poster-M4-harness-1080x1080.png
aivive-poster-M5-day-counter-1080x1080.png
aivive-poster-M5-day-counter-template.fig
```

存放路径:`outputs/poster/assets/`(成品)+ `outputs/poster/source/`(源文件)

---

## 7. 验收 checklist(出图前自检)

- [ ] **零紫色**(任何 hue 240-300° 都不行)
- [ ] **零红色**(error 也用 coral-700)
- [ ] **没有真人脸 / 政治符号 / 儿童**
- [ ] **没有马 / 马蹄 / 红色 horse 相关**
- [ ] **没有"AI 套路图"**(机器人脸、电路板、大脑齿轮、紫色 orb)
- [ ] **背景是 ink-950 (#08100E)**,不是纯黑 #000
- [ ] **Aivive / Give / Vive 这三个词出现时是衬线斜体**(IBM Plex Serif italic)
- [ ] **渐变只用 aqua → coral 2-stop**(不是 3-stop)
- [ ] **图标 stroke = 1.5px**(若用 lucide 风格)
- [ ] **有"留白"**,不堆满
- [ ] **三个调性词(Alive / Warm / Sharp)能在视觉上感觉到至少 2 个**

---

> 文案来源:推文 SSOT `outputs/tweet/推文.md`
> 品牌系统:`wiki/design/aivive-design.md`
> 完整内容 bank:`wiki/ops/social-content-bank-v1-mystery-phase.md`

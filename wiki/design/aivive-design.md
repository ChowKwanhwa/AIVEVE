---
title: Aivive Design System (DESIGN.md)
type: design
status: draft v0.2
tags: [design, brand, aivive, design-system, ssot]
sources:
  - raw/重启/项目方重启信息.md
  - wiki/design/references/framer-DESIGN.md
  - wiki/design/references/linear-DESIGN.md
  - wiki/design/references/cal-DESIGN.md
updated: 2026-04-20
---

# Aivive Design System

> **单一事实源(Single Source of Truth)**。所有 [[aivive]] 相关 UI / 前端 / 营销物料的视觉决策以本文档为准。
> 本 DESIGN.md 遵循 Google Stitch 提出的 DESIGN.md 约定:纯文本、面向 AI coding agents 可读、无特殊工具依赖。
>
> 采用本文档的场景:[[aivive-website]]、[[aivive-whitepaper]]、Dapp Demo、社媒模板、交易所 KYC 资料、[[brand-direction|品牌 VI 物料]]。

---

## 1. Brand Essence

### 1.1 One-liner

> **Aivive — the AI that gives.**

### 1.2 Dual reading(双关释义,两个都要用)

| Reading | 含义 | 出现场景 |
|---|---|---|
| **AI + Give** | 通过 AI 分享价值 | 产品叙事、落地页主文案、白皮书绪论 |
| **AI + Vive** | 鲜活、有生命的 AI | 品牌视觉基调、motion 语言、口号 subhead |

详见 [[brand-direction]] 和 [[ai-social-positioning]]。

### 1.3 Visual Adjectives(三个视觉形容词锁死调性)

1. **Alive** — 有呼吸、有脉冲、有光。**不**死寂、**不**静态。
2. **Warm** — 有人味、能分享。**不**企业、**不**冷峻。
3. **Sharp** — 结构清晰、信息密度高。**不**松散、**不**meme。

### 1.4 Inspirations(从 awesome-design-md 里挑的 3 份参考,各取一部分)

| 参考 | 取 | 不取 |
|---|---|---|
| [[framer-DESIGN|Framer]] | 渐变、motion、大字号、有机几何 | 不取"设计工具"自我叙事 |
| [[linear-DESIGN|Linear]] | 布局节奏、留白、组件冷静感 | 不取纯黑白极简(太冷) |
| [[cal-DESIGN|Cal.com]] | 色彩温度、文案语气、社区感 | 不取 productivity 框架 |

---

## 2. Color

深色模式为默认(Dapp / 官网主色),浅色模式备用(文档 / 白皮书)。

> **v0.2 色彩方向变更**:紫色(violet)退役,因"紫色 + 渐变 + AI" 是过度饱和的视觉刻板印象(OpenAI / Anthropic / Midjourney / Copilot 都在这个区间)。Aivive 改以 **aqua 生机青** 为主色,coral 作为暖点,用温度 + 生命体征区别于"紫色算力"叙事。

### 2.1 Brand Primary —— Aqua(生机青,承载 Alive + Vive)

| Token | Hex | 用途 |
|---|---|---|
| `--aqua-200` | `#A8FFEB` | 禁用态 / 柔和描边 |
| `--aqua-400` | `#7AFFE2` | 深色底上的 hover / 柔光 / 次级强调 |
| `--aqua-500` | `#4FFFD8` | **主色锚点**。深底 CTA、品牌强调、logo halo、呼吸环 |
| `--aqua-600` | `#1FE6B8` | 中调,深底 CTA 的 hover 深化 |
| `--aqua-700` | `#0E9E80` | 浅底 CTA / 浅底 brand text(WCAG AA on white) |
| `--aqua-800` | `#0B7A63` | 浅底深色调 |
| `--aqua-900` | `#08584A` | 深色发光衰减锚 |

> Aqua-500 `#4FFFD8` 是品牌"照片级锚点",所有 hero / logo / KV 发光皆以此为核心。

### 2.2 Warm Accent —— Coral(暖调,承载 Give + Warm)

| Token | Hex | 用途 |
|---|---|---|
| `--coral-500` | `#FF8A5C` | 温度锚点。"Give" 关键词、奖励/空投 UI、社区引导、渐变暖端 |
| `--coral-400` | `#FFA37D` | hover |
| `--coral-300` | `#FFBC9D` | 背景渐变柔端 |
| `--coral-600` | `#E86A3C` | 浅底 CTA(warning/give) |

### 2.3 Ink / Neutrals(去紫色化,中性略偏冷)

| Token | Hex | 用途 |
|---|---|---|
| `--ink-950` | `#08100E` | 深色模式 base 背景(取代旧 `#0B0720` 紫黑) |
| `--ink-900` | `#0F1816` | 深色面板底 |
| `--ink-800` | `#18221F` | 深色 raised surface |
| `--ink-700` | `#242F2C` | 深色 muted surface |
| `--ink-500` | `#5E6A67` | 次级文本(两个 mode 共用) |
| `--ink-300` | `#BFC7C4` | 深色底主文本 |
| `--ink-100` | `#E7EBEA` | 浅色 muted surface |
| `--ink-50` | `#F4F6F5` | 浅色模式 base 背景 |
| `--ink-0` | `#FFFFFF` | 纯白 / 浅色 raised surface |

> 旧版 ink 色带有明显紫色基调(HSL hue ≈ 260),与 violet 主色绑定。v0.2 改为 hue ≈ 160(微偏 teal)的中性暗色,与 aqua 主色和谐但不抢戏;文字色仍保持接近纯灰,确保可读性。

### 2.4 Semantic

| Token | Hex | 语义 |
|---|---|---|
| `--success` | `#4FFFD8` | (= aqua-400)—— 有生命 = 成功 |
| `--warning` | `#FF8A5C` | (= coral-500)—— 温暖色同时承担提示 |
| `--danger` | `#FF4470` | 错误、合约拒绝、余额不足 |
| `--info` | `#0E9E80` | (= aqua-700,浅底可读)—— 信息提示 |

### 2.5 Gradients(品牌 signature,v0.2 简化为 aqua↔coral 二色)

```
/* Primary gradient —— hero / logo halo / KV 主视觉 */
--grad-brand: linear-gradient(135deg, #4FFFD8 0%, #FF8A5C 100%);

/* Soft gradient —— 卡片 / banner / 轻量装饰 */
--grad-soft: linear-gradient(135deg, #7BFFE3 0%, #FFBC9D 100%);

/* Glow gradient —— 发光元素(按钮 hover halo、logo 呼吸) */
--grad-glow: radial-gradient(circle at 50% 50%, rgba(79,255,216,0.55) 0%, rgba(255,138,92,0.22) 45%, transparent 75%);
```

> 为什么只有二色:三色渐变里 violet→coral→aqua 的中段会产生"AI 彩虹"感(Midjourney 同款)。退 violet 后,aqua→coral 保留了温差(冷青→暖珊瑚),视觉上更像清晨/傍晚的自然光带,契合 §10 Moodboard 的"warm evening"意象。

### 2.6 颜色禁区(Do Not)

- ❌ **不使用紫色**(v0.2 退役,违反品牌差异化,会撞 AI 同质化审美)
- ❌ **不使用任何红色**(Red Horse 遗产色,必须视觉切断;danger `#FF4470` 是粉红色系,不是大红)
- ❌ **不使用纯黑 `#000`**(太硬,用 `--ink-950`)
- ❌ **不使用企业蓝**(Stripe/Coinbase 蓝会劝退 Solana 社区,且容易和 aqua 打架)
- ❌ **饱和黄不做强调色**(meme 感)
- ❌ **渐变不超过两色**(避免彩虹感)

---

## 3. Typography

### 3.1 字体栈

```
--font-sans: "Geist", "Inter", system-ui, -apple-system, sans-serif;
--font-serif: "IBM Plex Serif", "Source Serif Pro", Georgia, serif;
--font-mono: "Geist Mono", "JetBrains Mono", ui-monospace, monospace;
```

- **主字体 Geist**:承载 95% 的文本。现代、中性、有科技感但不冷。
- **衬线字体 IBM Plex Serif**:**仅**用于关键词级强调 —— 当 "Give" / "Vive" / "Aivive" 作为一个单独的词出现在大标题里,用衬线体。其他地方**不用**。
- **等宽 Geist Mono**:合约地址、代码、tokenomics 数字表格。

### 3.2 Type Scale

| Token | Size / Line-height | 字重 | 用途 |
|---|---|---|---|
| `display` | 64 / 72 | 700 | Hero 主标题 |
| `h1` | 48 / 56 | 700 | 页面主标题 |
| `h2` | 36 / 44 | 600 | 章节标题 |
| `h3` | 28 / 36 | 600 | 子章节 |
| `h4` | 22 / 30 | 600 | 卡片标题 |
| `body-lg` | 18 / 28 | 400 | 副标题 / 长文正文 |
| `body` | 16 / 26 | 400 | 标准正文 |
| `body-sm` | 14 / 22 | 400 | 辅助文本 |
| `caption` | 12 / 18 | 500 | 标签、元信息 |
| `mono` | 14 / 22 | 500 | 代码 / 合约地址 |

### 3.3 字符间距

- display / h1:`letter-spacing: -0.02em`
- h2 / h3:`letter-spacing: -0.015em`
- body 及以下:默认
- caption / label:`letter-spacing: 0.02em`,可配合 `text-transform: uppercase`

### 3.4 衬线用法范例

```html
<h1>
  The AI that <span class="font-serif italic">gives</span>.
</h1>

<h1>
  Keep AI <span class="font-serif italic">alive</span>, keep community <span class="font-serif italic">warm</span>.
</h1>
```

---

## 4. Spacing & Layout

### 4.1 Spacing Scale(4px base)

| Token | px |
|---|---|
| `space-0` | 0 |
| `space-1` | 4 |
| `space-2` | 8 |
| `space-3` | 12 |
| `space-4` | 16 |
| `space-5` | 20 |
| `space-6` | 24 |
| `space-8` | 32 |
| `space-10` | 40 |
| `space-12` | 48 |
| `space-16` | 64 |
| `space-20` | 80 |
| `space-24` | 96 |
| `space-32` | 128 |

### 4.2 Breakpoints

| Token | min-width |
|---|---|
| `sm` | 640 |
| `md` | 768 |
| `lg` | 1024 |
| `xl` | 1280 |
| `2xl` | 1536 |

### 4.3 Container

- 内容最大宽度:`1200px`
- 两侧 gutter:mobile `24px`,desktop `48px`
- 正文测量宽度(reading width):`68ch` 上限

---

## 5. Radii & Elevation

### 5.1 Radii

| Token | px | 用途 |
|---|---|---|
| `radius-xs` | 4 | 徽章、tag |
| `radius-sm` | 8 | 输入框、按钮 |
| `radius-md` | 12 | 按钮(大)、小卡片 |
| `radius-lg` | 20 | 卡片、模态 |
| `radius-xl` | 32 | Hero 容器、panel |
| `radius-pill` | 9999 | 胶囊按钮、头像 |

### 5.2 Shadows(浅色模式)

```
--shadow-1: 0 1px 2px rgba(8,16,14,0.06), 0 1px 3px rgba(8,16,14,0.08);
--shadow-2: 0 4px 10px rgba(8,16,14,0.08), 0 2px 4px rgba(8,16,14,0.06);
--shadow-3: 0 12px 32px rgba(8,16,14,0.12), 0 6px 14px rgba(8,16,14,0.08);
```

### 5.3 Glows(品牌 signature,按钮/logo/AI 正在工作的元素)

```
--glow-aqua:  0 0 40px rgba(79,255,216,0.50);   /* 主发光,取代旧 --glow-violet */
--glow-coral: 0 0 32px rgba(255,138,92,0.40);
```

> v0.2 退役 `--glow-violet`。所有引用点(logo breathe / focus ring / hero halo)统一切 `--glow-aqua`。

---

## 6. Motion

### 6.1 Durations

| Token | ms | 典型用途 |
|---|---|---|
| `duration-xs` | 120 | micro-interaction (hover color) |
| `duration-sm` | 200 | 按钮、链接过渡 |
| `duration-md` | 320 | 卡片展开、tooltip |
| `duration-lg` | 480 | 模态、侧滑抽屉 |
| `duration-xl` | 720 | 页面过渡、hero reveal |
| `duration-pulse` | 2800 | **呼吸**:logo、loading、AI 思考指示 |

### 6.2 Easing

```
--ease-organic:  cubic-bezier(0.2, 0.8, 0.2, 1);  /* 品牌标准 */
--ease-in-soft:  cubic-bezier(0.4, 0, 1, 1);
--ease-out-soft: cubic-bezier(0, 0, 0.2, 1);
--ease-breathe:  cubic-bezier(0.45, 0, 0.55, 1); /* 呼吸动画专用 */
```

### 6.3 Signature animations

1. **Breathe(呼吸)** —— logo mark 持续 2.8s 循环放大缩小 1.5%,同时 `--glow-aqua` 半径随之波动。承载"AI is alive"叙事。
2. **Flow(流动)** —— hero 背景中 3–5 个柔和 orb(aqua / coral 混)沿大椭圆轨道缓慢漂移(30s+ 单次)。
3. **Give(给予)** —— 空投 / 奖励相关 UI 出现时,`--coral-500` 粒子从 CTA 按钮向用户头像方向飞行,持续 800ms。

### 6.4 Motion 禁区

- ❌ 不用弹跳(bounce / overshoot)—— 太 playful,不匹配 "sharp"
- ❌ 不用长 > 1s 的 UI 过渡(pulse 例外)—— 用户会觉得卡
- ❌ 不用旋转 loading(spinning wheel)—— 用 breathe 取代

---

## 7. Iconography & Illustration

### 7.1 Icon

- **Library**:Lucide (首选)/ Phosphor (备选)
- **Stroke**:1.5px
- **Size scale**:16 / 20 / 24 / 32
- **Corner style**:rounded
- **专有符号**:Aivive mark = 一个被光晕环绕的呼吸环 / 脉冲波形 —— 由设计师交付矢量原件,**不在本文档定稿**,但需符合 §1.3 三个 visual adjectives,halo 颜色用 `--aqua-400`(不再使用 violet)。

### 7.2 Illustration style

✅ 采用:

- 3D 玻璃态 orbs(aqua → coral 渐变,**不加第三色**)
- 发光粒子 / 光带(aqua 为主,coral 点缀)
- 渐变网格(gradient mesh)背景,aqua↔coral 温差
- 抽象曲面(matching "有机" adjective)

❌ 避免:

- 扁平矢量插画(flat vector)—— 太 SaaS
- 线条插画(line illustration)—— 太冷
- 机器人 / 电路板 / 神经网络可视化 —— AI 陈词滥调
- emoji 堆砌 / 贴纸 —— 廉价 meme 感
- 任何**马**的意象 —— 阻碍新品牌叙事
- 紫色发光 / 紫色粒子 —— v0.2 禁用

---

## 8. Tone of Voice

### 8.1 原则

1. **Human-scale**:人话,不企业话
2. **Direct**:一句话讲清好处,不绕
3. **Warm**:允许有温度,不装冷静
4. **Confident**:不谦虚到让人怀疑

### 8.2 示例

| ❌ 不要 | ✅ 要 |
|---|---|
| "Leverage AI to enhance community engagement." | "The AI actually gives back. That's it." |
| "Our tokenomics empower long-term value accrual." | "55% goes to the community. Here's why." |
| "Cutting-edge membership infrastructure." | "Your on-chain identity, yours to keep." |
| "Join our vibrant ecosystem." | "Come in. Stay a while." |

### 8.3 品牌词表

以下词**总是大写首字母**作为专有名词使用,且可在视觉里用衬线体强调:

- **Aivive**
- **Give**(当承载品牌含义时)
- **Vive**(当承载品牌含义时)

其他场景按普通语法。

---

## 9. Components

### 9.1 Button

| 变体 | 底色 | 文字 | 边框 | Hover |
|---|---|---|---|---|
| `primary`(dark) | `--aqua-400` | `--ink-950` | — | +`--glow-aqua`, bg→`--aqua-300` |
| `primary`(light) | `--aqua-700` | `--ink-0` | — | +`--glow-aqua`(半径减半), bg→`--aqua-800` |
| `give` | `--coral-500` | `--ink-0` | — | +`--glow-coral`(只用于奖励/空投相关 CTA) |
| `ghost`(dark) | transparent | `--aqua-300` | 1px `--aqua-300` | bg→rgba(79,255,216,0.08) |
| `ghost`(light) | transparent | `--aqua-700` | 1px `--aqua-700` | bg→rgba(14,158,128,0.08) |
| `quiet` | `--ink-100` (light) / `--ink-800` (dark) | `--ink-900` / `--ink-300` | — | 加深 1 级 |

- radius: `radius-sm`(小)/ `radius-md`(中、大)
- Padding: `12px 20px`(中)/ `16px 28px`(大)
- 字重:500 或 600
- **primary 按钮在深底上的文字必须是 ink-950**(aqua 太亮,白字不可读)

### 9.2 Card

- 底色:`--ink-0`(light) / `--ink-800`(dark)
- 边框:1px `--ink-100` / `--ink-700`
- 圆角:`radius-lg`
- 阴影:`--shadow-2`
- Padding:`space-6` 或 `space-8`

### 9.3 Input

- 底色:`--ink-50` / `--ink-900`
- 圆角:`radius-md`
- 边框:1px `--ink-100` / `--ink-700`
- Focus:1px `--aqua-400`(dark)/ `--aqua-700`(light) + `--glow-aqua`(半径减半)

### 9.4 Badge / Tag

- 圆角:`radius-pill`
- Padding:`4px 10px`
- 字号:`caption`
- 变体:信息(aqua 半透)/ 成功(aqua 半透)/ 温暖(coral 半透)/ 危险(danger 半透)

### 9.5 Hero(页面英雄区)

- 背景:`--ink-950` 基础上叠加 `--grad-glow`(固定 2–3 个 aqua / coral orb)
- **不**铺 `--grad-brand` 全屏(违反 §9 "Don't"),渐变只作发光
- 主标题:`display` 尺寸,Sans + 关键词衬线
- CTA:1 primary(aqua) + 1 ghost,并排
- 必含 motion:**Flow** 动画

---

## 10. Mode

### 10.1 Dark mode(Dapp / 官网默认)

- 背景:`--ink-950`
- 主文本:`--ink-300`(约 L\*80,略去饱和,纯灰)
- 次级文本:`--ink-500`
- Brand text:`--aqua-300`
- 所有 aqua / coral 发光在深底上更鲜明,**不压低饱和**

### 10.2 Light mode(白皮书 / 文档 / 博客)

- 背景:`--ink-50`
- 主文本:`--ink-900`
- 次级文本:`--ink-500`
- Brand text:`--aqua-700`(保证 AA 对比)
- Primary button 改用 `--aqua-700`(浅底 `--aqua-400` 看不见)
- 渐变降饱和 10%,避免刺眼

### 10.3 选择规则

| 场景 | Mode |
|---|---|
| Dapp 主界面 | Dark |
| 官网落地页 | Dark |
| 白皮书 / Docs | Light |
| 博客 / 媒体稿 | Light |
| 社媒封面 | Dark(对比强,易识别) |

---

## 11. Consumption —— AI Agent 如何使用本文档

### 11.1 对 coding agent

在生成任何 [[aivive]] 相关的 UI 代码前,读本文档,按 §2–§9 使用 token(不直接写 hex,而是通过 CSS variables / Tailwind config 引用)。

### 11.2 对设计师

按 §1 确认调性,按 §2–§6 取值,按 §9 组件规范落稿。Logo mark 的具体矢量不在本文档范围,但需遵循 §1.3 三个 visual adjectives 与 §7.1 的"呼吸环/脉冲波"方向,halo 主色为 `--aqua-400`。

### 11.3 对营销 / 内容

按 §8 tone of voice 写文案。品牌词(§8.3)务必大写 + 在关键位置用衬线体。

### 11.4 实现参考(Tailwind / CSS 变量)

推荐把本文档 §2 / §4 / §5 / §6 的 token 直接落到 `tailwind.config.ts` 的 `theme.extend.colors / spacing / borderRadius / boxShadow / transitionDuration / transitionTimingFunction`,实现"改 token 即改全站"。

---

## 12. Open questions / 未定项

1. **中文名**尚未定(项目方未填)。本文档英文品牌视觉已可用,但**中文名敲定前**,所有中文文案中暂以 "Aivive" 原词出现,不做音译。详见 [[aivive]] / [[brand-direction]]。
2. **域名拼写**:`aiavive.ai` vs `aivive.ai` 未澄清,详见 [[aivive-website]]。本文档所有示意 URL 以占位 `aivive.*` 书写,最终发布前替换。
3. **Logo mark 矢量**尚未产出,§7.1 只给方向(halo = aqua),不锁造型。
4. **动态 Breathe 动画的节奏**(2.8s)基于成人平静呼吸频率,待可用性测试微调。
5. **Advisor / 站台人头像**是否需要专属视觉模版(见 [[relaunch-plan]] 站台议题),暂未定。
6. **是否需要第三个 brand 色填补 violet 空位** —— v0.2 目前只有 aqua + coral。若未来发现单靠二色不够承载数据可视化 / 分层信息,可补入 `teal-deep #0A6B5A` 作为 aqua 的"深夜"变体,而非引入新 hue。

---

## 13. Versioning

- **v0.1(2026-04-18)** —— 初始骨架,基于 Framer / Linear / Cal.com 合成;violet 为主色,aqua/coral 为强调色。
- **v0.2(2026-04-20)** —— 去紫色化。aqua 升为主色,violet 退役并加入禁区。原因:紫色 + 渐变 + AI 是同质化刻板印象(OpenAI / Anthropic / Midjourney / Copilot 同款),违反 §1.3 三个 adjectives 里的视觉差异化诉求。影响面:
  - §2 全部颜色表重写
  - §5.3 `--glow-violet` → `--glow-aqua`
  - §9 Button / Input / Hero 组件色位映射调整
  - §10 Dark / Light mode brand text 锚点迁移
  - 附属 Figma 文件(Visual Guide `buOQAK3El7SLaeSOEoOFjj` + Brand Brief `zUkPA30Kxd2pI2Tq143yAo`)的 `color/bg/brand`、`color/text/brand`、`color/text/on-brand`、三个 gradient 同步重建
- 下一版目标:v0.5 —— 补入定稿 Logo、完整组件库截图、首批 social kit 模板

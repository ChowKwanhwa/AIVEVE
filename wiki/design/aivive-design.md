---
title: Aivive Design System (DESIGN.md)
type: design
status: draft v0.1
tags: [design, brand, aivive, design-system, ssot]
sources:
  - raw/重启/项目方重启信息.md
  - wiki/design/references/framer-DESIGN.md
  - wiki/design/references/linear-DESIGN.md
  - wiki/design/references/cal-DESIGN.md
updated: 2026-05-05
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

| Reading             | 含义              | 出现场景                                |
| ------------------- | ----------------- | --------------------------------------- |
| **AI + Give** | 通过 AI 分享价值  | 产品叙事、落地页主文案、白皮书绪论      |
| **AI + Vive** | 鲜活、有生命的 AI | 品牌视觉基调、motion 语言、口号 subhead |

详见 [[brand-direction]] 和 [[ai-social-positioning]]。

### 1.3 Visual Adjectives(三个视觉形容词锁死调性)

1. **Alive** — 有呼吸、有脉冲、有光。**不**死寂、**不**静态。
2. **Warm** — 有人味、能分享。**不**企业、**不**冷峻。
3. **Sharp** — 结构清晰、信息密度高。**不**松散、**不**meme。

### 1.4 Inspirations(从 awesome-design-md 里挑的 3 份参考,各取一部分)

| 参考            | 取        | 不取                           |
| --------------- | --------- | ------------------------------ |
| [[framer-DESIGN | Framer]]  | 渐变、motion、大字号、有机几何 |
| [[linear-DESIGN | Linear]]  | 布局节奏、留白、组件冷静感     |
| [[cal-DESIGN    | Cal.com]] | 色彩温度、文案语气、社区感     |

---

## 2. Color

深色模式为默认(Dapp / 官网主色),浅色模式备用(文档 / 白皮书)。

### 2.1 Brand Primaries

| Token            | Hex         | 用途                                                      |
| ---------------- | ----------- | --------------------------------------------------------- |
| `--violet-500` | `#5B3BEE` | **主色**。按钮、链接、品牌强调。来自 "AI = 紫=算力" |
| `--violet-400` | `#7A60F2` | Hover / 次级强调                                          |
| `--violet-600` | `#4828D9` | Pressed / 深按                                            |
| `--violet-300` | `#9B86F7` | 禁用态 / 柔和描边                                         |
| `--violet-700` | `#3617B3` | 深色底上的暗紫                                            |

### 2.2 Warm Accent(对应 "Give")

| Token           | Hex         | 用途                                                     |
| --------------- | ----------- | -------------------------------------------------------- |
| `--coral-500` | `#FF8A5C` | 温度锚点。用于 "Give" 关键词、奖励/空投相关 UI、社区引导 |
| `--coral-400` | `#FFA37D` | hover                                                    |
| `--coral-300` | `#FFBC9D` | 背景渐变起点                                             |

### 2.3 Life Accent(对应 "Vive")

| Token          | Hex         | 用途                                                      |
| -------------- | ----------- | --------------------------------------------------------- |
| `--aqua-500` | `#4FFFD8` | 生命体征色。用于脉冲、光晕、成功态、AI 正在思考的 loading |
| `--aqua-400` | `#7BFFE3` | 柔光                                                      |
| `--aqua-600` | `#1FE8BC` | 高对比场景(小字 on dark)                                  |

### 2.4 Ink / Neutrals

| Token         | Hex         | 用途                       |
| ------------- | ----------- | -------------------------- |
| `--ink-950` | `#0B0720` | 深色模式 base 背景         |
| `--ink-900` | `#100A2B` | 深色面板底                 |
| `--ink-800` | `#1A1435` | 深色 raised surface        |
| `--ink-700` | `#261D46` | 深色 muted surface         |
| `--ink-500` | `#5E527E` | 次级文本(深色底)           |
| `--ink-300` | `#C6BDE1` | 深色底主文本               |
| `--ink-100` | `#EAE4F6` | 极浅紫灰                   |
| `--ink-50`  | `#F6F4FC` | 浅色模式 base 背景         |
| `--ink-0`   | `#FFFFFF` | 纯白 / 浅色 raised surface |

### 2.5 Semantic

| Token         | Hex         | 语义                                 |
| ------------- | ----------- | ------------------------------------ |
| `--success` | `#4FFFD8` | (= aqua-500)—— 有生命 = 成功       |
| `--warning` | `#FF8A5C` | (= coral-500)—— 温暖色同时承担提示 |
| `--danger`  | `#FF4470` | 错误、合约拒绝、余额不足             |
| `--info`    | `#5B3BEE` | (= violet-500)—— 信息提示          |

### 2.6 Gradients(品牌 signature,务必保留)

```
/* Primary gradient — 品牌主渐变,hero / logo-mark / CTA 发光使用 */
--grad-brand: linear-gradient(135deg, #5B3BEE 0%, #FF8A5C 50%, #4FFFD8 100%);

/* Soft gradient — 卡片 / banner / 轻量装饰 */
--grad-soft: linear-gradient(135deg, #9B86F7 0%, #FFBC9D 100%);

/* Glow gradient — 发光元素(按钮 hover halo、logo 呼吸) */
--grad-glow: radial-gradient(circle at 50% 50%, rgba(79,255,216,0.55) 0%, rgba(91,59,238,0.25) 40%, transparent 70%);
```

### 2.7 颜色禁区(Do Not)

- ❌ **不使用任何红色**(Red Horse 遗产色,必须视觉切断)
- ❌ **不使用纯黑 `#000`**(太硬,用 `--ink-950`)
- ❌ **不使用企业蓝**(Stripe/Coinbase 蓝会劝退 Solana 社区)
- ❌ **饱和黄不做强调色**(meme 感)

---

## 3. Typography

### 3.1 字体栈

```
--font-sans: "Geist", "Inter", system-ui, -apple-system, sans-serif;
--font-serif: "Instrument Serif", "Source Serif Pro", Georgia, serif;
--font-mono: "Geist Mono", "JetBrains Mono", ui-monospace, monospace;
```

- **主字体 Geist**:承载 95% 的文本。现代、中性、有科技感但不冷。
- **衬线字体 Instrument Serif**:**仅**用于关键词级强调 —— 当 "Give" / "Vive" / "Aivive" 作为一个单独的词出现在大标题里,用衬线斜体。其 italic 极其优美,与"warm + alive"调性相符。其他地方**不用**。
- **等宽 Geist Mono**:合约地址、代码、tokenomics 数字表格。

### 3.2 Type Scale

| Token       | Size / Line-height | 字重 | 用途              |
| ----------- | ------------------ | ---- | ----------------- |
| `display` | 64 / 72            | 700  | Hero 主标题       |
| `h1`      | 48 / 56            | 700  | 页面主标题        |
| `h2`      | 36 / 44            | 600  | 章节标题          |
| `h3`      | 28 / 36            | 600  | 子章节            |
| `h4`      | 22 / 30            | 600  | 卡片标题          |
| `body-lg` | 18 / 28            | 400  | 副标题 / 长文正文 |
| `body`    | 16 / 26            | 400  | 标准正文          |
| `body-sm` | 14 / 22            | 400  | 辅助文本          |
| `caption` | 12 / 18            | 500  | 标签、元信息      |
| `mono`    | 14 / 22            | 500  | 代码 / 合约地址   |

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

| Token        | px  |
| ------------ | --- |
| `space-0`  | 0   |
| `space-1`  | 4   |
| `space-2`  | 8   |
| `space-3`  | 12  |
| `space-4`  | 16  |
| `space-5`  | 20  |
| `space-6`  | 24  |
| `space-8`  | 32  |
| `space-10` | 40  |
| `space-12` | 48  |
| `space-16` | 64  |
| `space-20` | 80  |
| `space-24` | 96  |
| `space-32` | 128 |

### 4.2 Breakpoints

| Token   | min-width |
| ------- | --------- |
| `sm`  | 640       |
| `md`  | 768       |
| `lg`  | 1024      |
| `xl`  | 1280      |
| `2xl` | 1536      |

### 4.3 Container

- 内容最大宽度:`1200px`
- 两侧 gutter:mobile `24px`,desktop `48px`
- 正文测量宽度(reading width):`68ch` 上限

---

## 5. Radii & Elevation

### 5.1 Radii

| Token           | px   | 用途             |
| --------------- | ---- | ---------------- |
| `radius-xs`   | 4    | 徽章、tag        |
| `radius-sm`   | 8    | 输入框、按钮     |
| `radius-md`   | 12   | 按钮(大)、小卡片 |
| `radius-lg`   | 20   | 卡片、模态       |
| `radius-xl`   | 32   | Hero 容器、panel |
| `radius-pill` | 9999 | 胶囊按钮、头像   |

### 5.2 Shadows(浅色模式)

```
--shadow-1: 0 1px 2px rgba(11,7,32,0.06), 0 1px 3px rgba(11,7,32,0.08);
--shadow-2: 0 4px 10px rgba(11,7,32,0.08), 0 2px 4px rgba(11,7,32,0.06);
--shadow-3: 0 12px 32px rgba(11,7,32,0.12), 0 6px 14px rgba(11,7,32,0.08);
```

### 5.3 Glows(品牌 signature,按钮/logo/AI 正在工作的元素)

```
--glow-violet: 0 0 40px rgba(91,59,238,0.45);
--glow-coral: 0 0 32px rgba(255,138,92,0.40);
--glow-aqua: 0 0 32px rgba(79,255,216,0.45);
```

---

## 6. Motion

### 6.1 Durations

| Token              | ms   | 典型用途                                  |
| ------------------ | ---- | ----------------------------------------- |
| `duration-xs`    | 120  | micro-interaction (hover color)           |
| `duration-sm`    | 200  | 按钮、链接过渡                            |
| `duration-md`    | 320  | 卡片展开、tooltip                         |
| `duration-lg`    | 480  | 模态、侧滑抽屉                            |
| `duration-xl`    | 720  | 页面过渡、hero reveal                     |
| `duration-pulse` | 2800 | **呼吸**:logo、loading、AI 思考指示 |

### 6.2 Easing

```
--ease-organic: cubic-bezier(0.2, 0.8, 0.2, 1);  /* 品牌标准 */
--ease-in-soft: cubic-bezier(0.4, 0, 1, 1);
--ease-out-soft: cubic-bezier(0, 0, 0.2, 1);
--ease-breathe: cubic-bezier(0.45, 0, 0.55, 1);  /* 呼吸动画专用 */
```

### 6.3 Signature animations

1. **Breathe(呼吸)** —— logo mark 持续 2.8s 循环放大缩小 1.5%,同时 `--glow-violet` 半径随之波动。承载"AI is alive"叙事。
2. **Flow(流动)** —— hero 背景中 3–5 个柔和 orb 沿大椭圆轨道缓慢漂移(30s+ 单次)。
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
- **专有符号**:Aivive mark = 一个被光晕环绕的呼吸环 / 脉冲波形 —— 由设计师交付矢量原件,**不在本文档定稿**,但需符合 §1.3 三个 visual adjectives。

### 7.2 Illustration style

✅ 采用:

- 3D 玻璃态 orbs(violet → coral → aqua 渐变)
- 发光粒子 / 光带
- 渐变网格(gradient mesh)背景
- 抽象曲面(matching "有机" adjective)

❌ 避免:

- 扁平矢量插画(flat vector)—— 太 SaaS
- 线条插画(line illustration)—— 太冷
- 机器人 / 电路板 / 神经网络可视化 —— AI 陈词滥调
- emoji 堆砌 / 贴纸 —— 廉价 meme 感
- 任何**马**的意象 —— 阻碍新品牌叙事

---

## 8. Tone of Voice

### 8.1 原则

1. **Human-scale**:人话,不企业话
2. **Direct**:一句话讲清好处,不绕
3. **Warm**:允许有温度,不装冷静
4. **Confident**:不谦虚到让人怀疑

### 8.2 示例

| ❌ 不要                                           | ✅ 要                                    |
| ------------------------------------------------- | ---------------------------------------- |
| "Leverage AI to enhance community engagement."    | "The AI actually gives back. That's it." |
| "Our tokenomics empower long-term value accrual." | "55% goes to the community. Here's why." |
| "Cutting-edge membership infrastructure."         | "Your on-chain identity, yours to keep." |
| "Join our vibrant ecosystem."                     | "Come in. Stay a while."                 |

### 8.3 品牌词表

以下词**总是大写首字母**作为专有名词使用,且可在视觉里用衬线体强调:

- **Aivive**
- **Give**(当承载品牌含义时)
- **Vive**(当承载品牌含义时)

其他场景按普通语法。

---

## 9. Components

### 9.1 Button

| 变体        | 底色                                         | 文字                          | 边框                 | Hover                                      |
| ----------- | -------------------------------------------- | ----------------------------- | -------------------- | ------------------------------------------ |
| `primary` | `--violet-500`                             | white                         | —                   | +`--glow-violet`, bg→`--violet-400`   |
| `give`    | `--coral-500`                              | white                         | —                   | +`--glow-coral`(只用于奖励/空投相关 CTA) |
| `ghost`   | transparent                                  | `--violet-500`              | 1px `--violet-500` | bg→rgba(91,59,238,0.08)                   |
| `quiet`   | `--ink-100` (light) / `--ink-800` (dark) | `--ink-900` / `--ink-300` | —                   | 加深 1 级                                  |

- radius: `radius-sm`(小)/ `radius-md`(中、大)
- Padding: `12px 20px`(中)/ `16px 28px`(大)
- 字重:500 或 600

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
- Focus:1px `--violet-500` + `--glow-violet`(半径减半)

### 9.4 Badge / Tag

- 圆角:`radius-pill`
- Padding:`4px 10px`
- 字号:`caption`
- 变体:信息(violet 半透)/ 成功(aqua 半透)/ 温暖(coral 半透)

### 9.5 Hero(页面英雄区)

- 背景:`--grad-brand` 基础上叠加 `--grad-glow`(固定 2–3 个 orb)
- 主标题:`display` 尺寸,Sans + 关键词衬线
- CTA:1 primary + 1 ghost,并排
- 必含 motion:**Flow** 动画

---

## 10. Mode

### 10.1 Dark mode(Dapp / 官网默认)

- 背景:`--ink-950`
- 主文本:`--ink-300`
- 次级文本:`--ink-500`
- 所有渐变保持原色,发光在深底上更明显

### 10.2 Light mode(白皮书 / 文档 / 博客)

- 背景:`--ink-50`
- 主文本:`--ink-900`
- 次级文本:`--ink-500`(同)
- 渐变降饱和 10%,避免刺眼

### 10.3 选择规则

| 场景          | Mode                |
| ------------- | ------------------- |
| Dapp 主界面   | Dark                |
| 官网落地页    | Dark                |
| 白皮书 / Docs | Light               |
| 博客 / 媒体稿 | Light               |
| 社媒封面      | Dark(对比强,易识别) |

---

## 11. Consumption —— AI Agent 如何使用本文档

### 11.1 对 coding agent

在生成任何 [[aivive]] 相关的 UI 代码前,读本文档,按 §2–§9 使用 token(不直接写 hex,而是通过 CSS variables / Tailwind config 引用)。

### 11.2 对设计师

按 §1 确认调性,按 §2–§6 取值,按 §9 组件规范落稿。Logo mark 的具体矢量不在本文档范围,但需遵循 §1.3 三个 visual adjectives 与 §7.1 的"呼吸环/脉冲波"方向。

### 11.3 对营销 / 内容

按 §8 tone of voice 写文案。品牌词(§8.3)务必大写 + 在关键位置用衬线体。

### 11.4 实现参考(Tailwind / CSS 变量)

推荐把本文档 §2 / §4 / §5 / §6 的 token 直接落到 `tailwind.config.ts` 的 `theme.extend.colors / spacing / borderRadius / boxShadow / transitionDuration / transitionTimingFunction`,实现"改 token 即改全站"。

---

## 12. Open questions / 未定项

1. **中文名**尚未定(项目方未填)。本文档英文品牌视觉已可用,但**中文名敲定前**,所有中文文案中暂以 "Aivive" 原词ve]] / [[brand-direction]]。
2. ~~**域名拼写**~~ ✅ 已解决(2026-04-26)— 域名 `aivive.ai`,详见 [[aivive-website]] §域名拼写决议。本文档统一使用 `aivive.ai`。
3. **Logo mark 矢量**尚未产出,§7.1 只给方向,不锁造型。
4. **动态 Breathe 动画的节奏**(2.8s)基于成人平静呼吸频率,待可用性测试微调。
5. **Advisor / 站台人头像**是否需要专属视觉模版(见 [[relaunch-plan]] 站台议题),暂未定。

---

## 13. Versioning

- v0.1(2026-04-18)—— 初始骨架,基于 Framer / Linear / Cal.com 合成;具体组件视觉(Logo / Illustration 原件)待 VI 提案后补入
- v0.2(2026-05-05)—— serif 由 IBM Plex Serif 改为 **Instrument Serif**(更贴 warm + alive 调性,italic 用于品牌关键词强调);新增本仓库内字体源 [`wiki/design/assets/fonts/`](./assets/fonts/),包含 Geist 4 字重 + Instrument Serif Regular/Italic + Geist Mono 2 字重,共 8 个 woff2,用于 Claude Design 网页项目和 [[aiavive-app]] 共同消费
- 下一版目标:v0.5 —— 补入定稿 Logo、完整组件库截图、首批 social kit 模板

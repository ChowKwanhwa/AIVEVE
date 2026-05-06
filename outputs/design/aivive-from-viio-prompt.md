# Aivive Landing Prompt — 改自 viio-astro 结构

> **来源**:[github.com/sijad/viio-astro](https://github.com/sijad/viio-astro)(38 stars,Astro + Three.js + ogl + GSAP + Lenis,demo 在 viio.pages.dev)。
> **保留**:11-section 结构、滚动叙事节奏、Marquee logo 带、StepsTimeline、Statements 4 callout、FAQ、Plans 卡片栅格。
> **替换**:全部颜色 / 字体 / 文案 / 配图 / 主题,改为符合 [[aivive-design]] v0.2 的 violet → coral → aqua + Geist + Instrument Serif 体系,叙事改为 **Aivive 的 Recursive AI Protocol + buyback-and-burn** 主题。

---

## ⚠️ 法律注意(必读)

viio-astro 的 README 明确写 **"non-commercial use only"**(仓库无 LICENSE 文件,以 README 为准)。Aivive 是商用 token 项目,**不能直接 fork / clone 当生产基底**。以下三条选一:

1. **结构 / 视觉参考路线(推荐)** — 拿这份 prompt 给 Claude Design,生成全新代码;section 切分、滚动节奏借鉴 viio,代码 100% 自写,**不引入 viio 的任何源文件**。section 编排本身不构成版权。
2. **联系作者购买商用授权** — 邮件 sijad,问 commercial license 报价。
3. **完全自建** — 不参考。

本 prompt 默认走路线 1。

---

## 一、Section 全览(垂直 11 段)

| # | viio section | Aivive section | 关键替换 |
|---|---|---|---|
| 1 | Header | Header | logo + nav + Launch app CTA |
| 2 | Hero "Build Faster. Launch Smarter." | Hero "The AI that *gives*" | 主叙事;玻璃 orb 替 viio 的 WebGL 主体 |
| 3 | Introducing | Manifesto | Recursive AI Protocol (RAP) 概念引入 |
| 4 | StepsTimeline (3 steps) | The Loop (3 steps) | Create → Revenue → Burn |
| 5 | Gallery (3 product screenshots) | What ships in V1 | Studio / Feed / Burn Ledger 3 张 App 截图 |
| 6 | Statements (4 callouts) | Why this is different | 4 条差异化主张 |
| 7 | 3 supporting sections | For creators / holders / open internet | 3 段受众细分 |
| 8 | Plans (Free $0 / Premium $20) | **Tokenomics distribution** | 不卖 SaaS,改成代币分配可视化 |
| 9 | FAQ | FAQ | 5 条对得上代币审核员关心的问题 |
| 10 | Marquee (8 logos) | Backed by / Built on | 链上基础设施 + 已上交易所 logo |
| 11 | Footer | Footer | 法律实体披露 + 合规 disclaimer |

---

## 二、视觉 token 替换(viio → aivive)

### 颜色
| viio(原色调推断) | Aivive token([[aivive-design]] §2) |
|---|---|
| 中性灰 / 冷色基调 | `--ink-950` `#0B0720` 深紫底 |
| 主色(若有蓝)| `--violet-500` `#5B3BEE` |
| 强调 | `--coral-500` `#FF8A5C`(Give 暖)+ `--aqua-500` `#4FFFD8`(Vive 活)|
| 文本 | `--ink-300` `#C6BDE1` body / `--ink-100` `#EAE4F6` heading |
| 渐变 | `--grad-brand: 135deg, violet→coral→aqua` |

### 字体
| viio | Aivive(§3.1) |
|---|---|
| 系统 sans / 自选 | **Geist** 400/500/600/700 |
| 装饰衬线(如有)| **Instrument Serif italic**,**只**用于 heading 内 1 个品牌词(`gives` / `Aivive` / `pays you back`)|
| 等宽 | **Geist Mono** 用于合约 / 数字 / caption |

### Motion
| viio 用 | Aivive 是否保留 |
|---|---|
| GSAP | ✅ 保留(scroll-trigger / timeline)|
| Lenis | ✅ 保留(平滑滚动)|
| Three.js / ogl 主体 WebGL | ❌ 砍掉,换成 CSS 渐变 orb + `.breathe` + `.flow`(同 [`aivive-landing-prompt.md`](./aivive-landing-prompt.md) §SIGNATURE MOTION)|
| RectReveal 滚动揭示 | ✅ 保留(改用 GSAP ScrollTrigger + clip-path)|
| ImageMarquee / TextMarquee 跑马灯 | ✅ 保留(用于 Section 10)|

### 排版规则(全局)
- **headings = sentence case**,只有 nav / 标签 / mono 用 uppercase + 0.02em tracking
- **品牌词 "Aivive"** 出现在正文或 heading 里时,**永远** 包 `<span class="font-serif italic">Aivive</span>`
- **每个主 heading 选 1 个词** 用 serif italic 强调(给视觉节奏)
- **container max-width 1200px**(viio 可能用 1280+,Aivive 收紧)

---

## 三、Section-by-section 文案规划

> 文案规则:遵循 [[aivive-design]] §8 tone of voice — Human-scale / Direct / Warm / Confident。**不**用 corporate buzzword,**不**用空洞褒义词。
> 每段都标了 viio 对应原句,方便对比理解。

---

### Section 1 — Header

**viio 原**:logo "VIIO" + Home / About / Contact + Login + Get Started

**Aivive**:
- 左:logo wordmark **"Aivive"**(Geist 600)+ 一个 16px `.breathe` halo 小球贴在 wordmark 右侧
- 中:nav(Geist 400, 14px, uppercase, tracking-0.02em, color `text-ink-300`,hover `text-aqua-500`):
  - **Product**
  - **Tokenomics**
  - **Burn ledger**
  - **Whitepaper**
  - **Blog**
- 右:`Launch app` CTA → `bg-violet-500 hover:bg-violet-400 rounded-md px-5 py-2.5`,`hover:shadow-[var(--glow-violet)]`
- 移动端:汉堡菜单,展开层用 `liquid-glass`

---

### Section 2 — Hero

**viio 原**:"Build Faster. Launch Smarter." + 副标 + Get Started

**Aivive**:

```
H1 (display, 64–88px, font-bold, text-ink-100):
  The AI that gives,
  not the AI that takes.

(其中 "gives" 包 <span class="font-serif italic text-coral-400">gives</span>)

Sub (body-lg, 18–20px, text-ink-300, max-w-[640px]):
  On Aivive, a programmable share of platform revenue
  is converted, on a public weekly schedule, into
  permanent on-chain destruction of $AVV.
  Verifiable on Solscan.

Eyebrow (Geist Mono, 12px, uppercase, tracking-0.08em, text-aqua-500):
  Solana SPL · Symbol $AVV

CTAs:
  Primary:  "Read the whitepaper"  → bg-violet-500
  Ghost:    "See the burn ledger"   → border-violet-500
```

**Visual**:
- 背景 = `mesh-bg` 渐变网格 + 3 个 `.flow / .flow-slow / .flow-fast` 飘浮 orb
- 中央 = 1 个 `.breathe` 大 orb(280px,`var(--grad-brand)`,blur-24px,opacity-40),坐落在 H1 后面
- 右上角 = 一个小写斜体 `Aivive` 用 `font-serif italic text-aqua-500 mix-blend-screen` 飘浮(参考 [`aivive-landing-prompt.md`](./aivive-landing-prompt.md) Hero 段 cursive accent)
- 滚动到 hero 末时 → GSAP ScrollTrigger 触发 fade-out + 下一段 fade-in

---

### Section 3 — Manifesto(替换 viio Introducing)

**viio 原**:"A platform designed to turn ideas into impact"

**Aivive**:

```
Eyebrow (mono caption, uppercase, text-aqua-500):
  The Recursive AI Protocol

H2 (h1 scale, 48–60px, sentence case, text-ink-100):
  Web2 AI moves value upward.
  Aivive is the opposite arrow.

(其中 "opposite arrow" 包 <span class="font-serif italic text-coral-400">opposite arrow</span>)

Body (body-lg, 2 段, max-w-[680px], text-ink-300):
  Today's AI tools extract value from the people who
  feed them — and route it to a handful of platforms,
  with no path back. The infrastructure, the attention,
  and the upside all collect at one end.

  Aivive flips the direction. Every prompt funds a
  token sink. A programmable share of platform
  revenue funds a token sink. The community owns
  the meter. The supply only goes one way — down.

CTA (text link, text-violet-400 hover:text-violet-300):
  → How the loop works
```

**Visual**:
- 背景 `bg-ink-900` + 1 个 `.flow-slow` orb 在右下
- 左侧 H2 + body + CTA;右侧空(留白突出 manifesto 重量)
- 滚到这段时 GSAP RectReveal 类型的 clip-path 揭示 H2

---

### Section 4 — The Loop(替换 viio StepsTimeline 3 columns)

**viio 原**:Set up in minutes / Collaborate without friction / Deliver measurable results

**Aivive**:

```
Eyebrow (mono, text-aqua-500):
  How the loop works

H2 (sentence case):
  Three steps. One direction.

3 columns(每列:序号大字 + 标题 + body + 1 个图标):

01 — Create on Aivive.
     Generate images, video, and voice from prompts.
     Pay in USDC on Base. Costs from $0.05 per generation.
     [icon: Sparkles]

02 — Revenue funds the burn.
     A programmable share of platform revenue, collected
     as USDC on Base, is bridged to Solana every week
     via Circle CCTP — a 0-trust burn-and-mint primitive.
     [icon: Repeat]

03 — Token supply shrinks.
     On Solana, that USDC swaps to $AVV via Jupiter and
     gets permanently destroyed via SPL Token Burn.
     Every transaction lives on Solscan, forever.
     [icon: Flame]

Footer link:
  → Read the technical breakdown · 14 pages · PDF
```

**Visual**:
- 三列 grid `lg:grid-cols-3 gap-12`
- 每列上方一个 96px `.breathe` orb,各列 orb 颜色不同:violet → coral → aqua
- 列与列之间用 SVG 虚线箭头连接(暗示流向),mobile 下垂直堆叠
- 序号字号巨大(96–128px),`font-sans font-bold text-ink-700`(几乎透明的暗紫,装饰用)

---

### Section 5 — What ships in V1(替换 viio Gallery)

**viio 原**:"Designed for teams that value clarity and speed" + 3 product screenshots + Try It Today

**Aivive**:

```
Eyebrow (mono, text-coral-400):
  V1 · ships June 20, 2026

H2:
  What you can do on day one.

Sub (body-lg, max-w-[640px]):
  Aivive V1 opens with three surfaces. Built lean,
  shipped on schedule, expanded by what creators
  actually do — not what a roadmap deck promised.

3 cards (lg:grid-cols-3 gap-6, each card uses .liquid-glass):

Card 1 — Studio
  Subtitle: Prompt → image / video / voice
  Body: Top-tier models on tap (FLUX, Imagen 4 Ultra,
        Luma Dream Machine). New users get 100 free
        credits. Burn what you generate, keep what
        you publish.
  Visual: screenshot placeholder of Studio UI
          (V0 = pure CSS gradient placeholder)

Card 2 — Feed
  Subtitle: Social, AI-native
  Body: Trending / Following / New. One tap to
        Remix. Like, save, follow. The feed your
        prompt fuels.
  Visual: screenshot placeholder of Feed UI

Card 3 — Burn Ledger
  Subtitle: The receipts page
  Body: Every weekly buyback-and-burn cycle, fully
        traced. USDC in (BaseScan), AVV burned
        (Solscan). One dashboard. Public forever.
  Visual: screenshot placeholder of /burn page

Footer CTA:
  Primary: "Open the app"     (变灰 + "Opens June 20" 提示直到 V1 ship)
  Ghost:   "Get notified"     (邮箱 leadgen)
```

**Visual**:
- 每张卡 hover 时 `.breathe` 略加快 + 阴影加深
- screenshots V0 用 CSS gradient placeholder(violet / aqua / coral 各一);V1 ship 后换真截图

---

### Section 6 — Why this is different(替换 viio Statements 4 callouts)

**viio 原**:Creative Firepower / Built for Speed / Trusted by Professionals / Simple, Transparent Pricing

**Aivive**:

```
H2 (sentence case):
  Four reasons this isn't another AI app.

4 callouts (lg:grid-cols-2 gap-10):

01 — Verifiable on chain.
     Every burn is an SPL Token Burn instruction
     with a Solscan link. No promises, no
     "will burn one day", no marketing receipts.
     [icon: ShieldCheck]

02 — Built for creators, not extractors.
     Tip, boost, share — the value loops back to
     who made the work. Web2 keeps the upside;
     Aivive routes it home.
     [icon: Heart]

03 — Aligned with $AVV holders.
     Platform usage = token sink. The more people
     create, the less $AVV exists. Held supply
     gains weight automatically.
     [icon: TrendingDown]

04 — No mercenary capital.
     No KOL allocations. No private rounds. No
     locked seed unlocks waiting to dump on you.
     Liquidity is public, vesting is on-chain,
     receipts on Solscan.
     [icon: Lock]
```

**Visual**:
- 每条卡是 `.liquid-glass` `rounded-xl p-8`,最上面 32px icon `text-aqua-500 stroke-1.5`
- 编号 `01–04` 用 `font-mono text-xs text-ink-500`

---

### Section 7 — Three supporting sections(viio 同名 3 段)

**viio 原**:For modern teams / Scales as you grow / Real outcomes

**Aivive**:三个交替对齐(zig-zag)的大段,每段一个 H3 + body + small CTA

```
─── Section 7a — For creators ─────────────────
H3:  Generate. Publish. Get rewarded.
Body: Your work funds the ecosystem you live in.
      Every prompt you run, every post that gets
      saved, every Remix downstream — all of it
      shows up in the burn ledger.
CTA:  → Browse the feed

─── Section 7b — For $AVV holders ─────────────
H3:  A deflationary anchor with public proof.
Body: 10,000,000,000 fixed supply. The only thing
      that changes is the burn count. No fee
      distribution to dilute, no rebase to confuse.
      Just supply going down, on Solscan, every week.
CTA:  → See the burn ledger

─── Section 7c — For the open internet ────────
H3:  AI tools should give back to the communities
     that train them.
Body: Aivive is one experiment in that direction.
      We don't claim to solve it for the whole web.
      We claim to ship one working loop on Solana
      and let the receipts speak.
CTA:  → Read the manifesto
```

**Visual**:
- 每段:左/右图位 + 右/左文字位(zig-zag)
- 图位 V0 用大幅 gradient orb(brand grad,blur,可包 1 个 `.breathe`);V1 后可换插图

---

### Section 8 — Tokenomics distribution(替换 viio Plans 定价)

**viio 原**:Free $0 / Premium $20 + 14-day trial

**Aivive**:**完全重做**。代币不是 SaaS。这段最关键 —— 上所审核员第一时间看的就是这块。

```
Eyebrow (mono, text-coral-400):
  Tokenomics

H2:
  Where the supply goes.

Sub:
  10,000,000,000 $AVV total. Fixed forever.
  The only thing that changes is the count of
  $AVV that gets burned each week.

→ 配 1 张大型 donut chart 或 horizontal stacked bar(用 React 画,数据驱动)

7 buckets(数据来自 [[aivive-tokenomics]]):

| Bucket                              | %    | Vesting              |
|-------------------------------------|------|----------------------|
| Ecosystem & Community Incentives    | 30%  | TGE 起线性,详见白皮书 |
| Airdrop / Marketing Campaigns       | 25%  | TGE 起线性            |
| Exchange Liquidity (KuCoin / BG)    | 18%  | TGE 全释放           |
| Team                                | 10%  | 2 mo cliff + 10 mo linear |
| Treasury / DAO Reserve              | 10%  | 2 mo cliff + 10 mo linear |
| Market Maker                        | 5%   | 协议绑定               |
| Advisors                            | 2%   | 4 mo cliff + 8 mo linear  |

Initial circulating: ~1B AVV (10% of total).

Footnote (小字 mono):
  No private round. No seed round. No back-room allocations.
  All buckets visible on Solana, all multisig signers public.

CTA:
  → Read the full tokenomics breakdown · 9 pages
  → View Squads multisig on Solscan
```

**Visual**:
- Donut chart 或 horizontal stacked bar 用 violet → coral → aqua 系列段
- Hover 每段 → 显示 % + bucket 名 + vesting tooltip
- 下方一行 mono 字打 token 合约地址(等部署后填),配 "Copy" 按钮

---

### Section 9 — FAQ(viio 同段)

**viio 原**:5 Q&A about platform purpose / plans / free tier / security / onboarding

**Aivive**:5 条对得上**审核员 + 散户 + KOL** 各方关心的问题。

```
H2 (sentence case):
  Questions you'd actually ask.

(Accordion 折叠组件,默认全收起,点开滑出)

Q1 — What is $AVV?
A:  A Solana SPL token (9 decimals, fixed supply
    10B AVV). It's the deflationary anchor of the
    Aivive platform. Token contract: [tba — fill after mainnet deploy].

Q2 — How does the burn work?
A:  Every week, an Inngest cron job adds up
    platform USDC revenue on Base. A programmable
    share of that gets bridged to Solana via
    Circle CCTP, swapped to $AVV via Jupiter, and
    burned via SPL Token Burn. The 2/3 multisig
    on each chain ensures no single key can move
    funds. Every step has a Solscan or BaseScan
    link.

Q3 — Where can I buy $AVV?
A:  Currently on MEXC. Target listings: KuCoin
    (Q3 2026), Bitget. After TGE in June 2026,
    on-chain liquidity will live on Raydium and
    aggregated by Jupiter.

Q4 — When does the app launch?
A:  Landing page: May 18, 2026. V1 dapp (Studio
    + Feed + Burn Ledger): June 20, 2026.
    Discord opens Q3 2026. The roadmap is in
    the whitepaper, with hard dates.

Q5 — Is this audited?
A:  Yes. Smart-contract audit submitted week 3
    of build, results published before TGE. The
    burn-and-bridge pipeline is reviewed before
    going to mainnet. Audit firm + report linked
    in the whitepaper appendix.
```

**Visual**:
- Accordion 用 shadcn/ui 默认样式 + 微调:展开图标用 `lucide ChevronDown`,展开动画 200ms `--ease-organic`
- 容器 `max-w-[760px]` 居中

---

### Section 10 — Built on / Listed on(替换 viio Marquee 8 logo)

**viio 原**:"Trusted by leading teams" + 8 个公司 logo 跑马灯

**Aivive**:**两条** 跑马灯 — 链上基础设施 + 已上 / 目标交易所

```
Eyebrow (mono, text-aqua-500):
  Built on — Listed on

第 1 行 marquee — 链上基础设施(向左滚):
  Solana · Circle CCTP · Jupiter · Squads Protocol ·
  Helius · Wormhole · Privy · Inngest · Vercel ·
  Cloudflare R2 · Supabase

第 2 行 marquee — 交易所 / 浏览器(向右滚,反向制造层次):
  MEXC (live) · KuCoin (target Q3) · Bitget (target Q4) ·
  Raydium · Solscan · BaseScan · Birdeye · Dune

Footnote (小字 mono center):
  $AVV currently trades on MEXC. New listings
  announced via @AIVIVEHQ on X.
```

**Visual**:
- 用 `magicuidesign/magicui` 的 `<Marquee />` 组件(2 行,反向,gradient mask 边缘渐隐)
- logo 全部用 lucide-react 或 SVG inline,**不**塞外部 png(防 404 + 速度)
- 单 logo 高度 ~28px,间距 48px

---

### Section 11 — Footer(viio 同段)

**viio 原**:logo + nav + © 2026 VIIO

**Aivive**:

```
Top row(grid 4 col on desktop, stacked on mobile):

Col 1 — Brand
  Logo: Aivive(Geist 600)+ breathing halo 小球
  Tagline: The AI that gives.
  X / Telegram / GitHub icon button row(.liquid-glass)

Col 2 — Product
  Studio
  Feed
  Burn ledger
  Pricing(internal credits 价目)
  Status

Col 3 — Token
  Tokenomics
  Whitepaper(PDF)
  Audit report
  Squads multisig (Solscan)
  Contract address

Col 4 — Company
  About
  Blog
  Press kit
  Brand assets
  Contact

────────────────────────────────────

Bottom row:
  Left:   © 2026 Aivive · Operated by Yu Network SRL
  Center: Terms · Privacy · Cookie
  Right:  Built on Solana · Powered by Base USDC

Disclaimer (小字 mono caption, text-ink-500, max-w-full):
  $AVV is a utility token used inside the Aivive
  platform. Not a security, not a financial product,
  not investment advice. Token availability varies
  by jurisdiction. See whitepaper appendix for
  jurisdiction list.
```

**Visual**:
- 背景 `bg-ink-900` 比 hero 略浅
- 顶部细 1px 渐变线 `linear-gradient(90deg, violet → aqua, transparent)` 作分隔

---

## 四、滚动 / 动效编排(GSAP + Lenis)

> viio 用 GSAP + Lenis 做整页滚动,Aivive 沿用同栈,但触发的对象换成 Aivive 的 orb / liquid-glass 元素。

| Section | Scroll trigger 行为 |
|---|---|
| Hero → Manifesto | hero 大 orb 缩小 + 上移,转成 Manifesto 段右下角的小 `.flow` orb |
| Manifesto H2 | clip-path RectReveal,字按行依次出 |
| The Loop 3 列 | 进入视口后依次 fade-up,延迟 0 / 200 / 400ms |
| What ships in V1 cards | 每张 card 进视口时 `.breathe` 速度短暂加倍(从 2.8s → 1.2s)持续 800ms,模拟"被看到时活了过来" |
| Why this is different | 4 个 callout `clip-path` 揭示,zig-zag 顺序 |
| Tokenomics donut | 滚动到位时 chart 从 0% 动画累加到 100%(2s,`--ease-organic`)|
| FAQ | 每条点开时 `.liquid-glass` 边缘渐变光环短暂亮一下(用 `--glow-violet` 100ms in / 600ms out)|
| Marquee | 不依赖 scroll,持续 60s 一周 loop;hover 时暂停 |

**全局 Lenis 配置**:
```js
new Lenis({ duration: 1.2, easing: t => 1 - Math.pow(1 - t, 3) });
```

---

## 五、Tech 栈实现建议(给到工程师)

> Claude Design 多半会出 **React + Tailwind + Framer Motion** 形态。如果你想真上线 production,有两条路:

### 路线 A — 留 viio 同栈(Astro + GSAP + Lenis + Three.js / R3F)
- ✅ 性能最好(Astro 默认 SSG,JS 按需)
- ✅ 复用 viio 的滚动节奏经验
- ❌ 学习曲线 + 必须从头写所有组件(不能直接 fork 受 license 限制)
- 适合:你愿意花 2–4 周让工程师吃 Astro 学习曲线

### 路线 B — Next.js + R3F + GSAP + Lenis(推荐,与 [[aivive-app]] 主栈一致)
- ✅ 与 dapp 主栈一致([[aivive-app]] 用 Next 16),代码共享(组件 / token / 布局工具)
- ✅ React 生态成熟,shadcn / magic ui / aceternity 直接装
- ❌ 比 Astro 慢一点(差距在生产环境基本看不出)
- 适合:**默认选这条**

### 必装包(路线 B 起手)
```json
{
  "dependencies": {
    "next": "^16.0.0",
    "react": "^19.0.0",
    "tailwindcss": "^4.0.0",
    "shadcn-ui": "latest",
    "@magicui/react": "latest",
    "framer-motion": "^11.0.0",
    "gsap": "^3.13.0",
    "lenis": "^1.3.0",
    "lucide-react": "^0.5.0"
  }
}
```
3D 部分**先不装** R3F / Three —— Aivive landing V0 用 CSS-only,3D 等 V1 后期再加。

---

## 六、Claude Design 使用步骤

1. 整段(自此文件第 "三、Section-by-section 文案规划" 起到第 "五、Tech 栈" 止)拷进 Claude Design
2. **From template → Animation** tab
3. Design system 下拉选 **Aivive Design System**
4. Project name:`aivive-landing-from-viio-v1`
5. Click Create
6. 出来后预览:检查 11 个 section 都在 + 文案准确 + 颜色对得上 violet/coral/aqua
7. 缺什么 → 在 Claude Design 内追问 prompt(它支持 iterative refine)
8. 满意后 → Export → 拿到 React 代码,工程师在 [[aivive-app]] repo 内 `apps/web/` 落地

---

## 七、Deliverables checklist

- [ ] 11 个 section 全部存在,顺序正确
- [ ] 颜色 100% 走 [[aivive-design]] §2 token,无任何 hex 字面量
- [ ] Geist + Instrument Serif italic + Geist Mono 全部加载
- [ ] 每个主 heading 有 1 个词用 serif italic(共 6 处:gives / opposite arrow / Aivive 出现处 / pays you back 等)
- [ ] **零 `<video>` 标签**,所有动效 = CSS keyframes + GSAP scroll trigger
- [ ] Hero / CTA 中央 orb 用 `.breathe` 2.8s
- [ ] Marquee 2 行(基础设施 + 交易所),反向滚动
- [ ] Tokenomics donut 数据 = [[aivive-tokenomics]] 真实分配,**不**硬编码假数据
- [ ] FAQ 5 条全部覆盖审核员关心的话题(token / burn 机制 / 流动性 / 上线时间 / 审计)
- [ ] Footer 含 Yu Network SRL 法律实体披露 + utility-token disclaimer
- [ ] **不**复用 viio 任何源代码 / 资源(license 限制)
- [ ] Lenis 平滑滚动 + GSAP ScrollTrigger 节奏齐
- [ ] 移动端(iPhone 13 测试)所有 section 可读,marquee 不爆栈

---

## 八、TBD / 后期需补

- **真实 App 截图**(Section 5 三张卡)— 等 [[aivive-app]] V1 ship(2026-06-20)后替换
- **Donut chart 数据接 wiki**(Section 8)— 等 [[aivive-tokenomics]] §Open questions 全部清掉后,数字稳定再出图
- **审计报告链接**(Section 9 Q5 + Footer)— 等 CertiK 报告出来填 URL
- **合约地址**(Hero eyebrow + Section 8 + Footer)— 等 Solana mainnet 部署后填
- **Squads multisig 地址**(Section 8 + Footer)— 等签名人 + 部署完填
- **白皮书 PDF 直链**(Footer + 多处 CTA)— [[aivive-whitepaper]] gitbook 站上线后填
- **`/burn` 公开页**(Hero CTA + Section 7b CTA)— [[buyback-burn-program]] V1.5 上,先用占位 anchor `#burn-coming-soon`
- **Mystery-phase 替换版**(用于 5/18 landing 上线第一周还没全公开 brand 时)— 我可以另写一份 `aivive-from-viio-mystery.md`

---

## 九、版本

- v0.1 — 2026-05-06 初版,基于 viio-astro main 分支(updated 2026-04-26)的 11-section 结构 + [[aivive-design]] v0.2 token + [[aivive-tokenomics]] 真实分配数据

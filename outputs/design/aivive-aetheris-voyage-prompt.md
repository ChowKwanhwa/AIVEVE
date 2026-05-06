# Aivive Landing Prompt — 改自 aetheris-voyage(保留视频版)

> **来源**:[`raw/设计/aetheris-voyage/prompt.md`](../../raw/设计/aetheris-voyage/prompt.md) — 原稿是 Cinematic Space-Travel 主题(2 section: Hero + Capabilities,带 cinematic 视频背景 + JS rAF crossfade + 逐字 BlurText 入场)。
> **保留**:全部技术 spec(CDN React + Framer Motion + 自定义 FadingVideo + BlurText)、`liquid-glass` / `liquid-glass-strong` 工具类、**两段视频 URL 原样不动**、Section 1+2 整体编排、所有动效参数。
> **替换**:**字体一项**(Barlow → Geist;Instrument Serif italic 本来就是 Aivive 字体,留)、**颜色 5 处**(白色为主 → 白 + aqua/coral 微点缀)、**全部文案**(太空 / 火星 / 摄影 → Aivive 的 RAP / buyback-and-burn / Studio·Feed·Burn Ledger)、**partner 名 + card tag**(虚构 → 真实链上基础设施 + 真实 V1 能力)。
>
> **怎么用**:整段拷贝 "## Build Prompt" 起到末尾,**贴进 Claude Design** → From template → Animation → 选 Aivive Design System(已有则选,没有就让它现场生成)。出来后视频自动加载、文案是 Aivive 的、字体 Geist + Instrument Serif italic、动效不变。

---

## 一、视频留 / 改 / 后期换

原稿 2 段 CloudFront 视频(都是太空 / cinematic 主题):

| Section | URL | 主题 | 跟 Aivive 调性匹配度 |
|---|---|---|---|
| Hero | `hf_20260418_080021_d598092b...mp4` | 火星航行 / 宇宙广角 | ⚠️ 不直接对应 violet/coral/aqua,但"未知 / 远方 / 新边界"叙事可借,作"Beyond extraction / 新经济边疆"的视觉隐喻 OK |
| Capabilities | `hf_20260418_094631_d30ab262...mp4` | 生产 / 制造类抽象镜头 | ⚠️ 基本中性,可塞 |

**用户已确认要保留 → URL 原封不动放回 prompt**。

如果你后期想**换成真正 on-brand 的视频**(violet/coral/aqua glass orbs、流体液面、抽象有机渐变面 —— 见 [[aivive-design]] §7.2 illustration style),不需要改 prompt 的任何代码逻辑,**只替换 2 个 URL** 即可。生成 prompt 直接套:

```
"abstract liquid glass surfaces, soft 3D orbs in deep violet,
warm coral, and aqua mint, slow camera drift, gradient mesh
ambient, dreamy, no characters, no horse, no robot, 4k cinematic,
1920x1080, 12 seconds loop"
```

走 fal.ai(Luma Dream Machine 或 Pika 2.0,~$0.30 / 段),挂 Cloudflare R2 / Vercel Blob。

---

## 二、Aetheris → Aivive 替换对照表

### 字体

| Aetheris | Aivive([[aivive-design]] §3.1)|
|---|---|
| Google Fonts: `Instrument+Serif:ital@0;1&family=Barlow:wght@300;400;500;600` | `Instrument+Serif:ital@0;1&family=Geist:wght@400;500;600;700&family=Geist+Mono:wght@400;500` |
| `font-heading` → Instrument Serif(italic 用)| ✅ 同 |
| `font-body` → **Barlow** | **Geist** |
| (新增)`font-mono` → Geist Mono | 用于 stats 数字辅文 + caption |

### 颜色

| Aetheris 原 | Aivive 替换 | 出处 |
|---|---|---|
| `text-white` 默认全白 | 默认仍 white(深视频底,白可读)| §10.1 dark mode |
| 无强调色,headline italic 也是 white | headline 内**单词级 italic** 用 `text-coral-300`(warm)或 `text-aqua-300`(alive)| §1.3 visual adjectives |
| Stats 大数字 white | 大数字 `text-aqua-300`(serif italic 自带光感)| §6.3 signature |
| Badge "New" white pill `bg-white text-black` | `bg-aqua-400 text-ink-950`(对得上品牌)| §2.3 |
| Primary CTA `liquid-glass-strong` 白底 | 同 + 内文 `text-white`,hover 加 `box-shadow: var(--glow-aqua)` | §5.3 |
| `body bg: #000` | `body bg: #0B0720`(--ink-950)| §2.7 不用纯黑 |
| 全部 `liquid-glass::before` 边框是纯白渐变 | **保留** —— 视频底上纯白边框最干净,不动 |

**禁区不变**(原稿写得对):无绿色 ✓ / 无渐变背景(避免与视频抢)✓。Aivive 唯一加的是:**single accent word 用 coral/aqua italic**,其他全保留。

### 文案叙事(全替换)

| Aetheris(太空 / 探险) | Aivive(RAP / buyback-and-burn) |
|---|---|
| Maiden Crewed Voyage to Mars Arrives 2026 | V1 dapp launches June 20, 2026 |
| Venture Past Our Sky Across the Universe | Across the loop, value finds its way *home*. |
| Discover the universe in ways once unimaginable... | A platform-native deflationary loop... |
| Start Your Voyage / View Liftoff | Read the whitepaper / Watch the loop in action |
| 34.5 Min Watch Time / 2.8B+ Users | 10B Fixed $AVV supply / Weekly Burn schedule |
| Aeon · Vela · Apex · Orbit · Zeno | Solana · Circle · Jupiter · Squads · Wormhole |
| Collaborating with top aerospace pioneers globally | Built on the most-audited primitives in crypto |
| Production evolved | Generation *loops back* |
| AI Scenery / Batch Production / Smart Lighting | Studio / Feed / Burn ledger |
| Natural Context · Photo Realism ... | FLUX & Imagen · 100 free credits ... |

---

## 三、Build Prompt(可直接拷贝到 Claude Design)

> 下面这部分是给 Claude Design 看的。从这条横线下面起到文件末尾,整段复制。

---

### Build Prompt: Aivive — Across the Loop

Build a single-page landing site with **six sections** (**Hero** + **Capabilities** + **The Loop** + **Why this is different** + **FAQ** + **Footer**). Sections 1+2 use looping background videos with custom JS crossfade. Sections 3–6 are video-free and rely on a CSS-only motion language (gradient orbs + breathing pulses) to keep page weight low and let the two video moments stand out. All sections share the same `liquid-glass` design system, Geist + Instrument Serif type stack, and Framer Motion entrance animations. The brand is **Aivive** — an AI social platform on Solana whose platform revenue feeds a public weekly buyback-and-burn of the $AVV token. **Token allocation, vesting schedule, and supply distribution are intentionally omitted from this page** — covered in the whitepaper instead, surfaced on the site after listing.

#### Tech stack (pinned, CDN-only)

```html
<script src="https://cdn.tailwindcss.com"></script>
<script src="https://unpkg.com/react@18.3.1/umd/react.development.js" integrity="sha384-hD6/rw4ppMLGNu3tX5cjIb+uRZ7UkRJ6BPkLpg4hAu/6onKUg4lLsHAs9EBPT82L" crossorigin="anonymous"></script>
<script src="https://unpkg.com/react-dom@18.3.1/umd/react-dom.development.js" integrity="sha384-u6aeetuaXnQ38mYT8rp6sbXaQe3NL9t+IBXmnYxwkUI2Hw4bsp2Wvmx4yRQF1uAm" crossorigin="anonymous"></script>
<script src="https://unpkg.com/@babel/standalone@7.29.0/babel.min.js" integrity="sha384-m08KidiNqLdpJqLq95G/LEi8Qvjl/xUYll3QILypMoQ65QorJ9Lvtp2RXYGBFj1y" crossorigin="anonymous"></script>
<script src="https://unpkg.com/framer-motion@11.11.17/dist/framer-motion.js"></script>
<script>window.Motion = window.FramerMotion;</script>
```

Body is `bg: #0B0720` (deep violet, NOT pure black). Page is a React app mounted on `#root`, all components are `<script type="text/babel">` files exporting via `window.X = X`.

#### Fonts

Google Fonts:
```
family=Instrument+Serif:ital@0;1&family=Geist:wght@400;500;600;700&family=Geist+Mono:wght@400;500&display=swap
```

Tailwind config adds:
- `font-heading` → `'Instrument Serif', serif` (always italic in use, for one-word brand accents inside headings: *home*, *loops back*, *Aivive*, *gives*)
- `font-body` → `'Geist', sans-serif` (default for everything)
- `font-mono` → `'Geist Mono', ui-monospace, monospace` (stats secondary text + captions + contract addresses)

Default border radius override: `DEFAULT: "9999px"` (so bare `rounded` → pill).

#### Liquid-glass utilities (exact CSS, in a `<style>` block)

Two variants — `.liquid-glass` (subtle, for nav/chips/cards) and `.liquid-glass-strong` (heavier blur, for primary CTA). The Aetheris white-tinted gradient stays — it reads cleanest over video backgrounds:

```css
.liquid-glass {
  background: rgba(255,255,255,0.01);
  background-blend-mode: luminosity;
  backdrop-filter: blur(4px);
  -webkit-backdrop-filter: blur(4px);
  border: none;
  box-shadow: inset 0 1px 1px rgba(255,255,255,0.1);
  position: relative;
  overflow: hidden;
}
.liquid-glass::before {
  content: "";
  position: absolute; inset: 0;
  border-radius: inherit;
  padding: 1.4px;
  background: linear-gradient(180deg,
    rgba(255,255,255,0.45) 0%,
    rgba(255,255,255,0.15) 20%,
    rgba(255,255,255,0) 40%,
    rgba(255,255,255,0) 60%,
    rgba(255,255,255,0.15) 80%,
    rgba(255,255,255,0.45) 100%);
  -webkit-mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
  -webkit-mask-composite: xor;
  mask-composite: exclude;
  pointer-events: none;
}
.liquid-glass-strong {
  /* same as .liquid-glass but: */
  backdrop-filter: blur(50px);
  box-shadow: 4px 4px 4px rgba(0,0,0,0.05), inset 0 1px 1px rgba(255,255,255,0.15);
}
.liquid-glass-strong::before {
  /* same gradient stops 0.5 / 0.2 / 0 / 0 / 0.2 / 0.5 */
}
```

#### FadingVideo component (custom JS crossfade, no CSS transitions)

Wraps a `<video autoPlay muted playsInline preload="auto">` starting at `opacity: 0`. Behavior:

- `FADE_MS = 500`, `FADE_OUT_LEAD = 0.55` seconds.
- `fadeTo(target, duration)` uses `requestAnimationFrame`; reads current opacity from `video.style.opacity` so each new fade resumes from wherever the last one left off. Each call calls `cancelAnimationFrame` on the previous rAF id before starting.
- On `loadeddata`: set opacity 0, `play()`, `fadeTo(1)`.
- On `timeupdate`: if `fadingOutRef` not set and `duration - currentTime <= 0.55 && > 0`, flip the ref and `fadeTo(0)`.
- On `ended`: set opacity 0; after `setTimeout(100ms)` reset `currentTime = 0`, `play()`, clear `fadingOutRef`, `fadeTo(1)`.
- `loop` attribute is OFF (we implement looping manually via `ended`).
- Cleanup on unmount: cancel rAF, remove listeners.

---

#### Section 1 — Hero (full viewport, deep-violet bg)

**Background video** (120% width/height, top-aligned, centered horizontally — focal point is the top of frame):
- `src`: `https://d8j0ntlcm91z4.cloudfront.net/user_38xzZboKViGWJOttwIXH07lWA1P/hf_20260418_080021_d598092b-c4c2-4e53-8e46-94cf9064cd50.mp4`
- class: `absolute left-1/2 top-0 -translate-x-1/2 object-cover object-top z-0`
- style: `{ width: "120%", height: "120%" }`

No overlay. `z-10` layer holds: Navbar → Hero content (`flex-1`, centered) → Partners.

**Navbar** (`fixed top-4`, `px-8 / lg:px-16`, `z-50`)
- Left: 48×48 `liquid-glass` circle with italic serif lowercase **"a"** (Instrument Serif).
- Center (desktop only): `liquid-glass` pill, `px-1.5 py-1.5`, holding 5 text links — **Product**, **The Loop**, **Burn ledger**, **Whitepaper**, **Blog** — each `px-3 py-2 text-sm font-medium text-white/90 font-body`. Followed by an aqua pill button **Launch app** + ArrowUpRight icon (`bg-aqua-400 text-ink-950 font-semibold whitespace-nowrap`, hover slightly brighter).
- Right: 48×48 invisible spacer to balance logo.

**Hero content** (centered, `pt-24 px-4`)

All animated with Framer Motion, `initial: {filter: blur(10px), opacity: 0, y: 20}`, easeOut.

- **Badge** (delay 0.4s): `liquid-glass rounded-full pill`. Contains aqua pill chip **"New"** (`bg-aqua-400 text-ink-950 px-3 py-1 text-xs font-semibold`) + text **"V1 dapp launches June 20, 2026"** (`text-sm text-white/90 pr-3`).

- **Headline** — BlurText component (word-by-word animation, see below). Text: **"Across the loop, value finds its way home."**
  Classes: `text-6xl md:text-7xl lg:text-[5.5rem] font-heading italic text-white leading-[0.8] max-w-2xl justify-center tracking-[-4px]`.
  **Override on the word `home`**: render that word with class `text-coral-300` (so the final word is the warm accent — read like "value finds its way *home*").

- **Subheading** (delay 0.8s, `mt-4 text-sm md:text-base text-white max-w-2xl font-body font-light leading-tight`):
  **"A platform-native deflationary loop. A programmable share of platform revenue feeds a weekly buyback-and-burn — $AVV permanently destroyed on Solana, payments routed via USDC on Base. Every transaction lives on chain."**

- **CTAs** (delay 1.1s, `flex items-center gap-6 mt-6`):
  - Primary: `liquid-glass-strong rounded-full px-5 py-2.5 text-sm font-medium text-white` with **"Read the whitepaper"** + ArrowUpRight (`h-5 w-5`). Hover adds `box-shadow: 0 0 32px rgba(79,255,216,0.45)` (--glow-aqua).
  - Secondary: bare text link (`text-white/90 hover:text-aqua-300`), **"Watch the loop in action"** + Play icon (`h-4 w-4`, filled).

- **Stats row** (delay 1.3s, `flex items-stretch gap-4 mt-8`): two `liquid-glass` cards, `p-5 w-[220px] rounded-[1.25rem]`, each:
  - Top: white 28×28 outline SVG icon (Lucide style, `stroke-1.5 stroke-current`):
    - Card 1 icon = **Coins** (stacked coins)
    - Card 2 icon = **Flame**
  - Bottom: large number in **Instrument Serif italic, color `text-aqua-300`** (`text-4xl tracking-[-1px] leading-none`):
    - Card 1: **"10B"** — label below: **"Fixed $AVV supply forever"** (`text-xs text-white font-body font-light mt-2`)
    - Card 2: **"Weekly"** — label below: **"Burn schedule, on chain"**

**Partners** (bottom of hero, delay 1.4s)
`flex flex-col items-center gap-4 pb-8`:
- `liquid-glass rounded-full chip` (`px-3.5 py-1 text-xs font-medium text-white`): **"Built on the most-audited primitives in crypto."**
- Row of 5 names in **Instrument Serif italic white**, `text-2xl md:text-3xl tracking-tight`, `gap-12/md:gap-16`:
  **Solana · Circle · Jupiter · Squads · Wormhole**

#### BlurText component (word-by-word blur-in)

`IntersectionObserver` triggers on 10% visibility. Splits text by spaces. Each word is a `motion.span` with:
- `initial: {filter: 'blur(10px)', opacity: 0, y: 50}`
- 3-step keyframes to `{filter: 'blur(5px)', opacity: 0.5, y: -5}` → `{filter: 'blur(0px)', opacity: 1, y: 0}`
- `duration: 0.7` (`stepDuration 0.35 × 2`), `times: [0, 0.5, 1]`, `ease: easeOut`
- Stagger: `delay = (i * 100) / 1000` seconds
- `display: inline-block`, `marginRight: 0.28em` (not non-breaking-space — letter-spacing -4px eats nbsp).

Parent `<p>` is `display: flex; flexWrap: wrap; justifyContent: center; rowGap: 0.1em`.

**Aivive override**: when the word matches one of `["home", "Aivive", "gives", "loops"]` (case-insensitive, strip punctuation), apply class `text-coral-300` if word is `home / gives` (warm accent), or `text-aqua-300` if word is `Aivive / loops` (life accent). The blur-in animation is identical; only the final color differs.

---

#### Section 2 — Capabilities (`min-h-screen`, deep-violet bg)

**Background video** (full-bleed, no 120% scale):
- `src`: `https://d8j0ntlcm91z4.cloudfront.net/user_38xzZboKViGWJOttwIXH07lWA1P/hf_20260418_094631_d30ab262-45ee-4b7d-99f3-5d5848c8ef13.mp4`
- class: `absolute inset-0 w-full h-full object-cover z-0`

Same FadingVideo treatment. No overlay.

**Content** (`relative z-10 px-8 md:px-16 lg:px-20 pt-24 pb-10 flex flex-col min-h-screen`):

**Header** (`mb-auto`):
- Kicker: `text-sm font-body text-white/80 mb-6` → `// Capabilities`
- Heading: `font-heading italic text-white text-6xl md:text-7xl lg:text-[6rem] leading-[0.9] tracking-[-3px]`:
  ```
  Generation
  loops back
  ```
  (two lines, `<br/>` between). **Override on the word `loops`**: render with class `text-aqua-300`.

**Three cards** (`grid grid-cols-1 md:grid-cols-3 gap-6 mt-16`): each is `liquid-glass rounded-[1.25rem] p-6 min-h-[360px] flex flex-col`.

**Top row of each card** (`flex items-start justify-between gap-4`):

- Left: 44×44 nested `liquid-glass` square (`rounded-[0.75rem]`) with a white Lucide-style outline SVG icon (`stroke-current strokeWidth=1.5 fill=none h-6 w-6`):
  - **Studio**: **Wand2** icon — `<svg viewBox="0 0 24 24" stroke-width="1.5" fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round"><path d="M15 4V2"/><path d="M15 16v-2"/><path d="M8 9h2"/><path d="M20 9h2"/><path d="M17.8 11.8L19 13"/><path d="M15 9h0"/><path d="M17.8 6.2L19 5"/><path d="m3 21 9-9"/><path d="M12.2 6.2 11 5"/></svg>`
  - **Feed**: **Newspaper** icon — `<svg viewBox="0 0 24 24" stroke-width="1.5" fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round"><path d="M4 22h16a2 2 0 002-2V4a2 2 0 00-2-2H8a2 2 0 00-2 2v16a2 2 0 01-2 2zm0 0a2 2 0 01-2-2v-9c0-1.1.9-2 2-2h2"/><path d="M18 14h-8"/><path d="M15 18h-5"/><path d="M10 6h8v4h-8z"/></svg>`
  - **Burn ledger**: **Flame** icon — `<svg viewBox="0 0 24 24" stroke-width="1.5" fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round"><path d="M8.5 14.5A2.5 2.5 0 0011 12c0-1.38-.5-2-1-3-1.072-2.143-.224-4.054 2-6 .5 2.5 2 4.9 4 6.5 2 1.6 3 3.5 3 5.5a7 7 0 11-14 0c0-1.153.433-2.294 1-3a2.5 2.5 0 002.5 2.5z"/></svg>`

- Right: `flex flex-wrap justify-end gap-1.5 max-w-[70%]` — 4 small `liquid-glass` pill tags (`rounded-full px-3 py-1 text-[11px] text-white/90 font-body whitespace-nowrap`):
  - Card 1: **FLUX & Imagen · 100 Free Credits · Image & Video · Pay in USDC**
  - Card 2: **Trending · Following · Remix · Save & Follow**
  - Card 3: **USDC In · AVV Out · Solscan · BaseScan**

**Middle**: `flex-1` spacer.

**Bottom of each card** (`mt-6`):

- Title `h3`: `font-heading italic text-white text-3xl md:text-4xl tracking-[-1px] leading-none` — **"Studio"** / **"Feed"** / **"Burn ledger"**
- Body `p` (`mt-3 text-sm text-white/90 font-body font-light leading-snug max-w-[32ch]`):
  - **"Top-tier image and video models on tap. Pay-as-you-go in USDC on Base. Every generation funds the burn — including the credits you spent yourself."**
  - **"A social feed for AI-native creators. One tap to Remix what inspires you. Like, save, follow. The work your prompt fuels."**
  - **"Every weekly buyback-and-burn cycle, fully traced. USDC in (BaseScan), $AVV burned (Solscan). The receipts page that never closes."**

---

#### Section 3 — The Loop (`min-h-screen`, deep-violet bg, no video)

The mechanism section. After Capabilities tells you *what* you can do, this tells you *why your $5 of credits actually matters*. No video — let the cinematic moments breathe and let the mechanism read with calm.

**Background**: solid `bg-ink-950` (#0B0720) + 3 large floating CSS gradient orbs, each `absolute rounded-full pointer-events-none`:
- Orb A — top-left, 640px, `background: radial-gradient(circle, rgba(91,59,238,0.55) 0%, rgba(91,59,238,0.15) 40%, transparent 70%)`, `blur-[120px]`, `opacity-55`, class `flow-slow`
- Orb B — center-right, 480px, `background: radial-gradient(circle, rgba(255,138,92,0.45) 0%, transparent 60%)`, `blur-[120px]`, `opacity-50`, class `flow`
- Orb C — bottom-left, 720px, `background: radial-gradient(circle, rgba(79,255,216,0.45) 0%, transparent 60%)`, `blur-[120px]`, `opacity-55`, class `flow-fast`

Add the keyframes once (in the `<style>` block):
```css
@keyframes flow {
  0%   { transform: translate(0, 0)        rotate(0deg); }
  33%  { transform: translate(40px, -30px) rotate(2deg); }
  66%  { transform: translate(-30px, 20px) rotate(-1deg); }
  100% { transform: translate(0, 0)        rotate(0deg); }
}
.flow      { animation: flow 28s cubic-bezier(0.2, 0.8, 0.2, 1) infinite; }
.flow-slow { animation: flow 42s cubic-bezier(0.2, 0.8, 0.2, 1) infinite; }
.flow-fast { animation: flow 18s cubic-bezier(0.2, 0.8, 0.2, 1) infinite; }
@media (prefers-reduced-motion: reduce) {
  .flow, .flow-slow, .flow-fast { animation: none; }
}
```

**Content** (`relative z-10 px-8 md:px-16 lg:px-20 pt-24 pb-24 max-w-[1200px] mx-auto`):

- Kicker: `text-sm font-body text-aqua-300/80 mb-6` → `// How the loop works`
- Heading (BlurText, same component as before, with `direction` mapped to `text-coral-300` italic):
  ```
  Three steps.
  One direction.
  ```
  Classes: `font-heading italic text-white text-5xl md:text-6xl lg:text-[5rem] leading-[0.95] tracking-[-3px] max-w-3xl`
- Sub (delay 0.4s, `mt-6 text-base md:text-lg text-white/80 font-body font-light max-w-2xl`):
  **"From prompt to permanent burn — what your $5 of credits actually does, in three on-chain hops."**

**Three step columns** (`grid grid-cols-1 md:grid-cols-3 gap-8 mt-20`):

Each column staggered by `0.2s`. Inside each column:

- Top: massive numeral `01 / 02 / 03` in `font-heading italic text-ink-700 text-[120px] md:text-[140px] leading-none mb-4` (almost transparent decorative — Aivive --ink-700 #261D46 against --ink-950 reads as "barely there")
- Title `h3`: `font-heading italic text-white text-3xl md:text-4xl tracking-[-1px] leading-tight mb-3`
  - Step 1: **"Create on Aivive."**
  - Step 2: **"Revenue funds the *bridge*."** (`bridge` wrapped in `text-coral-300`)
  - Step 3: **"Token supply *shrinks*."** (`shrinks` wrapped in `text-aqua-300`)
- Body `p`: `text-sm md:text-base text-white/80 font-body font-light leading-relaxed mb-6 max-w-[36ch]`
  - Step 1: **"Generate images, video, and voice from prompts. Pay in USDC on Base. Costs from $0.05 per generation. New users get 100 free credits."**
  - Step 2: **"A programmable share of platform USDC, collected on Base, is bridged to Solana every week via Circle CCTP — a 0-trust burn-and-mint primitive used by stablecoin issuers, not a third-party bridge."**
  - Step 3: **"On Solana, that USDC swaps to $AVV via Jupiter and gets permanently destroyed via SPL Token Burn. Every transaction lives on Solscan, forever."**
- Mono caption: `font-mono text-[11px] uppercase tracking-[0.08em] text-white/40 leading-relaxed`
  - Step 1: `Base mainnet · USDC · ~12s confirmation`
  - Step 2: `Circle CCTP · 0-trust · ~15min attestation`
  - Step 3: `Solana · Jupiter + SPL Burn · weekly`

**Bottom row** (delay 1.0s, centered, `mt-20`):
- Text link `text-sm text-white/70 hover:text-aqua-300 font-body inline-flex items-center gap-2`:
  **"Read the technical breakdown"** + ArrowUpRight icon (h-4 w-4) + small mono `· 14 pages · PDF` (`text-white/40 ml-2`)

---

#### Section 4 — Why this is different (`min-h-screen`, deep-violet bg, no video)

The credibility section. After **The Loop** tells you *how* the burn works, this tells you *why this isn't just another AI app with a token bolted on*. Four pillars. Each one runs whether anyone reads the marketing — mechanism, not promise.

> **Editorial constraint**: this section is intentionally **token-allocation-free**. No percentages, no vesting schedules, no fundraise structure. That all lives in the whitepaper, surfaced post-listing. The pillars below stand on posture and mechanism, not on numbers.

**Background**: solid `bg-ink-950` + 1 ambient orb top-right, 560px, brand gradient (`background: linear-gradient(135deg, rgba(91,59,238,0.35) 0%, rgba(255,138,92,0.20) 50%, rgba(79,255,216,0.15) 100%)`), `blur-[140px]`, `opacity-40`, class `flow-slow`.

**Content** (`relative z-10 px-8 md:px-16 lg:px-20 pt-24 pb-24 max-w-[1200px] mx-auto`):

- Kicker: `text-sm font-body text-coral-300/80 mb-6` → `// Why this is different`
- Heading (BlurText with `another` mapped to `text-coral-300` italic):
  **"Four reasons this isn't another AI app."**
  Classes: `font-heading italic text-white text-5xl md:text-6xl lg:text-[5rem] leading-[0.95] tracking-[-3px] max-w-3xl`
- Sub (delay 0.4s, `mt-6 text-base md:text-lg text-white/80 font-body font-light max-w-2xl`):
  **"Each one runs whether anyone reads the marketing. Mechanism, not promise."**

**Four callout cards** (`grid grid-cols-1 md:grid-cols-2 gap-6 mt-20`):

Each card: `liquid-glass rounded-[1.5rem] p-8 min-h-[260px] flex flex-col`. Stagger entry 150ms between cards. Initial `{opacity: 0, y: 30, filter: blur(8px)}`, animate to `{opacity: 1, y: 0, filter: blur(0px)}`, duration 0.6s easeOut.

Card structure:
- Top row (`flex items-start justify-between`):
  - Left: 40×40 nested `liquid-glass rounded-[0.75rem]` square containing a Lucide-style outline SVG icon (`h-6 w-6 text-white`, stroke 1.5)
  - Right: numeral `font-mono text-xs uppercase tracking-[0.08em] text-white/40` → **01 / 02 / 03 / 04**
- Title `h3` (`mt-6`): `font-heading italic text-white text-3xl md:text-4xl tracking-[-1px] leading-tight`
- Body `p` (`mt-3 text-sm md:text-base text-white/80 font-body font-light leading-relaxed max-w-[36ch]`)

**Card 01** — Icon: **ShieldCheck**
Title: **"Verifiable *on chain*."** (`on chain` → `text-aqua-300`)
Body: **"Every burn is an SPL Token Burn instruction with a Solscan link. No promises. No 'will burn one day.' No marketing receipts. Open the burn ledger and check."**

**Card 02** — Icon: **Heart**
Title: **"Built for creators, not *extractors*."** (`extractors` → `text-coral-300`)
Body: **"Tip, boost, share — the value loops back to who made the work. Web2 platforms keep the upside; Aivive routes it home."**

**Card 03** — Icon: **Repeat**
Title: **"A real loop, not a *slogan*."** (`slogan` → `text-coral-300`)
Body: **"The mechanism runs whether anyone reads the marketing. USDC in on Base. $AVV out on Solana. Cron-driven, multisig-gated, public from week one."**

**Card 04** — Icon: **Lock**
Title: **"Public from *day one*."** (`day one` → `text-aqua-300`)
Body: **"Multisig signers are named. Audit results are linked. The mechanism is reviewable before mainnet. No back-room rounds, no private side-deals — the structure is open from the moment we ship."**

**Bottom row** (delay 1.0s after cards, centered, `mt-16`):
- Bare text link: `text-sm text-white/70 hover:text-aqua-300 inline-flex items-center gap-2` → **"See the full mechanism in the whitepaper"** + ArrowUpRight (`h-4 w-4`)

---

#### Section 5 — FAQ (`min-h-screen`, deep-violet bg, no video)

Five questions that the smart skeptic asks. Accordion. Mostly text. Calm.

**Background**: solid `bg-ink-950` + 1 ambient orb bottom-left, 480px, `background: radial-gradient(circle, rgba(127,255,227,0.30) 0%, transparent 70%)`, `blur-[140px]`, `opacity-40`, class `flow-slow`.

**Content** (`relative z-10 px-8 md:px-16 lg:px-20 pt-24 pb-24 max-w-[860px] mx-auto`):

- Kicker: `text-sm font-body text-aqua-300/80 mb-6` → `// FAQ`
- Heading (BlurText with `actually` mapped to `text-aqua-300` italic):
  **"Questions you'd actually ask."**
  Classes: `font-heading italic text-white text-5xl md:text-6xl lg:text-[5rem] leading-[0.95] tracking-[-3px] mb-16`

**Accordion** (`flex flex-col gap-3`):

Each item is a `liquid-glass rounded-2xl overflow-hidden`. Header is a button (`w-full px-6 py-5 flex items-center justify-between text-left`):
- Left: question (`font-body font-medium text-white text-base md:text-lg`)
- Right: ChevronDown icon (`h-5 w-5 text-white/70 transition-transform duration-200`, rotates 180° when expanded)

Body (collapsible, `px-6 pb-6 text-sm md:text-base text-white/80 font-body font-light leading-relaxed`):

When expanded, the item gets an extra subtle inner glow: `box-shadow: inset 0 0 24px rgba(91,59,238,0.18)`. Body fades in over 200ms via Framer Motion (initial `opacity: 0, height: 0`, animate `opacity: 1, height: auto`).

**Q&A content** (5 items):

**Q1**: What is $AVV?
**A**: A Solana SPL token. Fixed supply, no inflation. The deflationary anchor of the Aivive platform — the only thing that changes is the count of tokens burned each week. Full contract details (address, decimals, mint authority status) are in the whitepaper appendix and published on this site after mainnet deploy.

**Q2**: How does the burn actually work?
**A**: Every week, an Inngest cron job adds up platform USDC revenue collected on Base. A programmable share gets bridged to Solana via Circle CCTP — Circle's own burn-and-mint primitive, the same one stablecoin issuers use. On Solana, the USDC swaps to $AVV via Jupiter and gets burned via the standard SPL Token Burn instruction. A 2/3 multisig on each chain ensures no single key can move funds. Every step has a Solscan or BaseScan link.

**Q3**: Where can I buy $AVV?
**A**: Currently on MEXC. Target listings: KuCoin (Q3 2026), Bitget. After TGE in June 2026, on-chain liquidity lives on Raydium and is aggregated by Jupiter.

**Q4**: When does the app launch?
**A**: Landing page is live now. V1 dapp (Studio + Feed + Burn ledger): June 20, 2026. Discord opens Q3 2026. The roadmap is in the whitepaper, with hard dates — not "Q-something" placeholder dates.

**Q5**: Is this audited?
**A**: Yes. The smart-contract audit was submitted in week 3 of build, with results published before TGE. The bridge-and-burn pipeline is reviewed before going to mainnet. The audit firm name and full report PDF live in the whitepaper appendix.

**Below accordion** (centered, mt-12):
- `font-body text-sm text-white/60` → **"Have a question we didn't answer?"**
- Bare text link: `text-aqua-300 hover:text-aqua-400 inline-flex items-center gap-2 mt-2` → **"Ask on Twitter @AIVIVEHQ"** + ArrowUpRight

---

#### Section 6 — Footer + Final CTA (`min-h-[80vh]`, gradient bg, no video)

The page closes here. One last CTA, a marquee for credibility, a 4-col link grid, legal disclaimer.

**Background**: `bg-ink-950` + a single large radial mesh overlay:
```css
background:
  radial-gradient(at 50% 30%, rgba(91,59,238,0.25) 0px, transparent 55%),
  radial-gradient(at 50% 90%, rgba(79,255,216,0.18) 0px, transparent 60%),
  #0B0720;
```

**Layer 1 — Final CTA** (`relative z-10 px-8 md:px-16 lg:px-20 pt-32 pb-16 text-center max-w-[900px] mx-auto`):

- Kicker: `font-heading italic text-aqua-300 text-3xl md:text-4xl tracking-[-1px] mb-4` → **"Get on the loop."**
- H2 (BlurText, `stay` mapped to `text-coral-300` italic):
  **"Open the app, watch the burn, stay a while."**
  Classes: `font-heading italic text-white text-4xl md:text-5xl lg:text-[4rem] leading-[1] tracking-[-2px] mb-6`
- Sub (delay 0.4s, `text-base md:text-lg text-white/80 font-body font-light max-w-xl mx-auto`):
  **"V1 ships June 20, 2026. Until then, read the docs and get on the early-access list."**
- 2 CTAs (`flex items-center justify-center gap-6 mt-8`):
  - Primary: `liquid-glass-strong rounded-full px-6 py-3 text-sm font-medium text-white` → **"Get notified"** + ArrowUpRight (`h-5 w-5`). Hover adds `box-shadow: 0 0 32px rgba(79,255,216,0.45)`.
  - Ghost: bare link, `text-sm text-white/90 hover:text-aqua-300 inline-flex items-center gap-2` → **"Read the whitepaper"** + ArrowUpRight (`h-4 w-4`).

**Layer 2 — Marquee row** (`relative z-10 mt-20 mb-16`):

A horizontal scrolling row of partner / infrastructure names. Implementation: a `<div>` with `overflow-hidden` containing two duplicated rows (so it loops seamlessly), each `flex items-center gap-16 whitespace-nowrap animate-marquee`.

Add keyframes:
```css
@keyframes marquee {
  0%   { transform: translateX(0); }
  100% { transform: translateX(-50%); }
}
.animate-marquee { animation: marquee 50s linear infinite; }
```

Names (each in `font-heading italic text-white/40 text-2xl md:text-3xl tracking-tight whitespace-nowrap`, separated by a small dot `·` in `text-white/20`):

**Solana · Circle CCTP · Jupiter · Squads · Wormhole · Helius · Privy · Inngest · MEXC · KuCoin · Bitget · BaseScan · Solscan · Birdeye**

Add fade-out gradient masks on left + right edges:
```css
mask-image: linear-gradient(90deg, transparent 0%, #000 8%, #000 92%, transparent 100%);
```

**Layer 3 — Footer link grid** (`relative z-10 px-8 md:px-16 lg:px-20 pt-12 pb-8 max-w-[1200px] mx-auto`):

`grid grid-cols-2 md:grid-cols-4 gap-12`:

**Col 1 — Brand**
- Logo: 40×40 `liquid-glass` circle with italic serif `a` (same as nav)
- Wordmark: `font-heading italic text-white text-xl mt-3` → **"Aivive"**
- Tagline: `text-sm text-white/60 font-body mt-1` → **"The AI that gives."**
- Social icons row (`flex gap-2 mt-5`): three 36×36 `liquid-glass` rounded-full buttons with white outline icons:
  - Twitter / X (Lucide `Twitter` SVG path)
  - Telegram (Lucide `Send` SVG path)
  - GitHub (Lucide `Github` SVG path)

**Col 2 — Product**
Header: `font-mono text-[11px] uppercase tracking-[0.08em] text-aqua-300/80 mb-4` → **"Product"**
Links (`flex flex-col gap-2 text-sm text-white/70 font-body hover:text-white`):
- Studio
- Feed
- Burn ledger
- Pricing
- Status

**Col 3 — On-chain**
Header: same style → **"On-chain"**
Links:
- Burn ledger
- Whitepaper
- Audit report
- Squads multisig
- Contract address

**Col 4 — Company**
Header: same style → **"Company"**
Links:
- About
- Blog
- Press kit
- Brand assets
- Contact

**Layer 4 — Legal bottom row** (`relative z-10 px-8 md:px-16 lg:px-20 pt-8 pb-10 border-t border-white/5 max-w-[1200px] mx-auto`):

`flex flex-col md:flex-row items-start md:items-center justify-between gap-4 text-xs font-body text-white/50`:

- Left: **© 2026 Aivive · Operated by Yu Network SRL**
- Center: `flex gap-5` → **Terms** · **Privacy** · **Cookie**
- Right: `font-mono text-[10px] uppercase tracking-[0.08em]` → **"Built on Solana · Powered by Base USDC"**

**Layer 5 — Disclaimer** (very bottom, `px-8 md:px-16 lg:px-20 pb-12 max-w-[900px] mx-auto`):

`font-mono text-[10px] uppercase tracking-[0.05em] text-white/30 leading-relaxed`:

**"$AVV is a utility token used inside the Aivive platform. Not a security, not a financial product, not investment advice. Token availability varies by jurisdiction. See whitepaper appendix for jurisdiction list. Aivive is operated by Yu Network SRL, a registered entity. Reach legal@aivive.ai for compliance inquiries."**

---

#### Icons (inline lucide-style SVGs, currentColor stroke)

- **ArrowUpRight**: 24×24, `M7 17L17 7` + `M7 7h10v10`, strokeWidth 2, round caps.
- **Play**: 24×24 filled polygon `6 4 20 12 6 20 6 4`.
- **Coins** (stats card 1): 24×24 stroke 1.5, two stacked circles — `<circle cx="8" cy="8" r="6"/><path d="M18.09 10.37A6 6 0 1 1 10.34 18"/><path d="M7 6h1v4"/><path d="M16.71 13.88l.7.71-2.82 2.82"/>`.
- **Flame** (stats card 2 + Section 2 card 3): see Section 2 SVG above.
- **ShieldCheck** (Section 4 card 01): 24×24, stroke 1.5, `<path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"/><polyline points="9 12 11 14 15 10"/>`.
- **Heart** (Section 4 card 02): 24×24, stroke 1.5, `<path d="M19 14c1.49-1.46 3-3.21 3-5.5A5.5 5.5 0 0 0 16.5 3c-1.76 0-3 .5-4.5 2-1.5-1.5-2.74-2-4.5-2A5.5 5.5 0 0 0 2 8.5c0 2.29 1.51 4.04 3 5.5l7 7Z"/>`.
- **Repeat** (Section 4 card 03): 24×24, stroke 1.5, `<path d="m17 2 4 4-4 4"/><path d="M3 11v-1a4 4 0 0 1 4-4h14"/><path d="m7 22-4-4 4-4"/><path d="M21 13v1a4 4 0 0 1-4 4H3"/>`.
- **Lock** (Section 4 card 04): 24×24, stroke 1.5, `<rect width="18" height="11" x="3" y="11" rx="2" ry="2"/><path d="M7 11V7a5 5 0 0 1 10 0v4"/>`.
- **ChevronDown** (Section 5 FAQ accordion): 24×24, stroke 1.5, `<polyline points="6 9 12 15 18 9"/>`.
- **Twitter / X** (Section 6 footer): 24×24, stroke 1.5, `<path d="M22 4s-1 2-3 3a4.5 4.5 0 0 0-8 4v1A10 10 0 0 1 3 5s-4 9 5 13a11 11 0 0 1-7 2c9 5 20 0 20-11.5 0-.3 0-.5-.1-.8A7 7 0 0 0 22 4z"/>`.
- **Send / Telegram** (Section 6 footer): 24×24, stroke 1.5, `<line x1="22" y1="2" x2="11" y2="13"/><polygon points="22 2 15 22 11 13 2 9 22 2"/>`.
- **Github** (Section 6 footer): 24×24, stroke 1.5, `<path d="M9 19c-5 1.5-5-2.5-7-3m14 6v-3.87a3.37 3.37 0 0 0-.94-2.61c3.14-.35 6.44-1.54 6.44-7A5.44 5.44 0 0 0 20 4.77 5.07 5.07 0 0 0 19.91 1S18.73.65 16 2.48a13.38 13.38 0 0 0-7 0C6.27.65 5.09 1 5.09 1A5.07 5.07 0 0 0 5 4.77a5.44 5.44 0 0 0-1.5 3.78c0 5.42 3.3 6.61 6.44 7A3.37 3.37 0 0 0 9 18.13V22"/>`.

#### Notes

- All text white by default; one-word italic accents in serif use `text-coral-300` (warm: home / gives / bridge / goes / stay) or `text-aqua-300` (life: loops / Aivive / shrinks / actually). No green, no rainbow gradient backgrounds — gradient only lives in CSS variables `--grad-brand / --grad-soft / --grad-glow` (do NOT use as decorative background; reserved for orbs / glows).
- **Sections 1+2** use FadingVideo for cinematic backgrounds. **Sections 3–6** are video-free — they use radial-gradient orbs with `.flow / .flow-slow / .flow-fast` keyframes (defined in Section 3 CSS block above). This rhythm — 2 video moments + 4 calm sections — keeps the page from feeling visually exhausting.
- No CSS transitions on the videos — fades must be rAF-driven per the FadingVideo spec.
- Videos are full-bleed with no dark overlay; contrast comes from the liquid-glass chrome.
- Body bg `#0B0720` (Aivive `--ink-950`), NOT pure black.
- `Launch app` nav button + Hero stats card 1 number "10B" + `Get notified` final CTA use `text-aqua-300` or `bg-aqua-400` — the only places aqua takes a saturated surface role; everywhere else aqua is text accent only.
- "Aivive" written anywhere as a brand wordmark must be in `font-heading italic` — applies to the footer wordmark in Section 6.
- All `.flow / .flow-slow / .flow-fast` and any pulse animation should be wrapped in `@media (prefers-reduced-motion: reduce) { ... animation: none; }` for accessibility.
- Framer Motion dev warnings about list keys can be suppressed with a console.error filter wrapper — they're benign.
- Section 4's 4 callout cards should animate **only when scrolled into view** (use IntersectionObserver, threshold 0.3) — staggered 150ms entry per card.
- Accordion in Section 5: only one item open at a time (clicking another closes the previous). Default state on load: all closed.
- Marquee in Section 6 pauses on hover (`group-hover:[animation-play-state:paused]`) so users can read names.

---

## 四、上线后还要补 / TBD

### 视觉素材
- **视频换 brand-aligned** — 见本文件第一节 "视频留 / 改 / 后期换";现 Section 1+2 的太空 / 晶簇视频是占位
- **Section 2 三张卡的真截图** — [[aivive-app]] V1 上线后,可在卡内角落加 thumbnail

### 数据 / 数字
- **Section 1 stats 真数据** — V1 ship + 第一周 burn 跑完后,把 "10B / Weekly" 升级为 "10B Total / X AVV burned to date"(注意:**仍不出 vesting / 分配 %**,只出累计 burn)
- **Tokenomics section** — 故意不在本 landing 出现。等正式上 KuCoin / 在白皮书里发布后,再决定是否在 landing 增补一段(可能用更精炼的 1-2 行无 chart 形式)

### 链上 / 合约
- **合约地址**(Section 6 footer) — 等 Solana mainnet 部署后填
- **Squads multisig 地址**(Section 6 footer) — 等签名人 + 部署完填
- **审计报告 URL**(Section 5 Q5 + Section 6 footer) — 等 CertiK 报告出来填

### CTA / 链接
- **`Launch app` nav CTA** — [[aivive-app]] V1 ship 前指 `/coming-soon`,ship 后指 `app.aivive.ai`
- **`Watch the loop in action` 二级 CTA** — 等 demo video 出后填,V0 可链 `/burn` 公开页
- **`Get notified` 邮箱 leadgen**(Section 6) — 接 Resend / ConvertKit,需后端 endpoint
- **Whitepaper PDF 直链**(多处) — [[aivive-whitepaper]] gitbook 站上线后填
- **"Read the technical breakdown · 14 pages · PDF"**(Section 3 footer) — 同上,等白皮书 finalize 后链具体页

### 内容 / 二级
- **Discord / X / Telegram icon** — Section 6 footer 已加 X · Telegram · Github 三个;Discord 暂不公开([[aivive-website]] 决议),后期 Q3 2026 上线后再加第 4 个
- **Mystery-phase 替换版** — 5/18 落地页第一周如果还在 mystery 阶段(品牌 / 团队 / 审计未全公开),Section 5 FAQ Q4 上线时间 + Q5 audit 部分可以暂时换 teaser 版("V1 ships soon" / "Audit report releasing pre-TGE")

---

## 五、版本

- v0.1 — 2026-05-06,基于 Aetheris Voyage prompt v1(2026-04-18)+ [[aivive-design]] v0.2 + [[aivive-tokenomics]] 真分配数据,初版 2 sections (Hero + Capabilities)
- v0.2 — 2026-05-06,扩展到 6 sections — 新增 The Loop / Tokenomics / FAQ / Footer,采用 video-free CSS-only motion 策略
- **v0.3 — 2026-05-06,移除 Tokenomics 段** — 用户决定不在 landing 阶段透露 token 分配 / vesting / 比例;Section 4 改为 **"Why this is different"**(4 个差异化主张:Verifiable on chain / Built for creators / A real loop / Public from day one),只讲机制和姿态,无任何数字。同步清理 Header nav("Tokenomics" → "The Loop")、Footer nav col 3("Token" → "On-chain",移除 Tokenomics 链接)、TBD 中相关条目、donut chart 实现细节。新增 4 个 SVG icons(ShieldCheck / Heart / Repeat / Lock)。


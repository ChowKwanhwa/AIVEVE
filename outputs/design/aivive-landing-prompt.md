# Aivive Landing Prompt — Claude Design(CSS-only / 无视频版)

> 改自 [`raw/设计/astronautPrompt.md`](../../raw/设计/astronautPrompt.md)(Orbis.Nft 暗空主题)。
> **保留**:4-section 结构、liquid-glass UI、card grid、texture overlay、整体动态感。
> **替换**:全部颜色 / 字体 / 文案 / 图标,改为符合 [[aivive-design]] v0.2 的 **violet → coral → aqua + Geist + Instrument Serif** 体系,主题改为 Aivive 的 AI 社交 + 回购销毁叙事。
> **关键变更(vs 原稿)**:**砍掉所有 video background**,改成纯 CSS 的 gradient orb + Breathe / Flow signature animation。理由:对得上 [[aivive-design]] §6.3 自有 motion 语言、零素材依赖、永远不会因 CDN 404 而塌、Linear / Cal.com / Stripe 这一档 2026 年也都已不用 stock motion video。Section 3 grid 卡只用 3 张静图(可后期生)。
> **怎么用**:整段拷贝到 Claude Design **From template → Animation** tab,选择已有的 Aivive Design System,直接 Create。Section 3 grid 卡先用 CSS gradient placeholder 出图,等 [[aivive-app]] V1 feed 有真实创作内容后再换。

---

Create a marketing landing page called **"Aivive — the AI that gives"** with 4 sections. Use a deep-violet brand theme (NOT navy blue, NOT pure black), 3D glass orbs, soft gradient halos, and a "liquid glass" UI effect. **No video backgrounds** — all motion is achieved via CSS keyframes on layered gradient orbs. The page is for an AI social platform on Solana whose platform revenue feeds a public weekly buyback-and-burn of the $AVV token. Recreate it exactly as described below.

## FONTS (Google Fonts + self-hosted woff2)

- **Geist** (Sans) — used for almost all UI text and headings. Aliased as `font-sans` in Tailwind. Weights needed: 400 / 500 / 600 / 700.
- **Instrument Serif** — used **only** for one-word brand accents inside headings (the words "*gives*", "*alive*", "*warm*", "*Aivive*"). Always italic. Aliased as `font-serif`. Weight 400 italic.
- **Geist Mono** — used for caption metadata, contract address strings, ticker tags, and any number-heavy element. Aliased as `font-mono`. Weights 400 / 500.

Load via Google Fonts in `index.html` (Instrument Serif italic + Geist + Geist Mono):

```
https://fonts.googleapis.com/css2?family=Geist:wght@400;500;600;700&family=Geist+Mono:wght@400;500&family=Instrument+Serif:ital@0;1&display=swap
```

(If Geist is unavailable on Google Fonts, use **Inter** as a safe substitute.)

**Casing rule**:
- Headings (display / h1 / h2): **sentence case**, NOT uppercase. (Warm + human-scale.)
- Caption / label / nav: `uppercase` + `tracking-[0.02em]`.
- Brand accent words inside headings: `font-serif italic`, sentence case.

## COLOR SYSTEM (Tailwind config)

Single source of truth: [`wiki/design/aivive-design.md`](../../wiki/design/aivive-design.md) §2.

```js
// tailwind.config.ts theme.extend.colors
{
  // Brand primaries (violet — main CTA, links, brand emphasis)
  violet: {
    300: '#9B86F7',
    400: '#7A60F2',
    500: '#5B3BEE', // PRIMARY brand color
    600: '#4828D9',
    700: '#3617B3',
  },
  // Warm accent — "Give" word, airdrop / community CTAs
  coral: {
    300: '#FFBC9D',
    400: '#FFA37D',
    500: '#FF8A5C',
  },
  // Life accent — "Vive" word, AI thinking pulse, success
  aqua: {
    400: '#7BFFE3',
    500: '#4FFFD8', // pulse / glow
    600: '#1FE8BC',
  },
  // Ink (neutrals — dark mode default)
  ink: {
    0:   '#FFFFFF',
    50:  '#F6F4FC',
    100: '#EAE4F6',
    300: '#C6BDE1', // primary text on dark
    500: '#5E527E', // secondary text on dark
    700: '#261D46', // muted surface
    800: '#1A1435', // raised surface
    900: '#100A2B', // panel
    950: '#0B0720', // BASE BACKGROUND (NOT #000, NOT navy blue)
  },
  danger: '#FF4470',
}
```

**Gradients** (CSS variables on `:root`):

```css
--grad-brand: linear-gradient(135deg, #5B3BEE 0%, #FF8A5C 50%, #4FFFD8 100%);
--grad-soft:  linear-gradient(135deg, #9B86F7 0%, #FFBC9D 100%);
--grad-glow:  radial-gradient(circle at 50% 50%,
              rgba(79,255,216,0.55) 0%,
              rgba(91,59,238,0.25) 40%,
              transparent 70%);
```

**Color forbiddens** (do NOT use):
- ❌ Red of any kind (project's previous brand was red — must visually break from it). `--danger` only used inside semantic error UI, never decoratively.
- ❌ Pure black `#000` — too hard, use `--ink-950` (#0B0720).
- ❌ Corporate blue (Stripe / Coinbase blue) — wrong audience signal.
- ❌ Saturated yellow as accent — meme energy.
- ❌ Neon green as decorative accent (the original Orbis prompt used #6FFF00 — replace with `aqua-500` `#4FFFD8` everywhere).

## LIQUID GLASS CSS EFFECT

Applied via a `.liquid-glass` class on the navbar, social icon buttons, content cards, and overlay bars. Tinted slightly violet, NOT pure white.

```css
.liquid-glass {
  background: rgba(155, 134, 247, 0.04); /* faint violet wash */
  backdrop-filter: blur(14px) saturate(140%);
  -webkit-backdrop-filter: blur(14px) saturate(140%);
  border: none;
  box-shadow:
    inset 0 1px 1px rgba(234, 228, 246, 0.10),
    0 1px 0 rgba(91, 59, 238, 0.08);
  position: relative;
  overflow: hidden;
}
.liquid-glass::before {
  content: '';
  position: absolute;
  inset: 0;
  border-radius: inherit;
  padding: 1.4px;
  background: linear-gradient(180deg,
    rgba(234, 228, 246, 0.45) 0%,
    rgba(155, 134, 247, 0.15) 20%,
    rgba(255, 255, 255, 0) 40%,
    rgba(255, 255, 255, 0) 60%,
    rgba(127, 255, 227, 0.18) 80%,
    rgba(234, 228, 246, 0.45) 100%);
  -webkit-mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
  -webkit-mask-composite: xor;
  mask-composite: exclude;
  pointer-events: none;
}
```

## TEXTURE OVERLAY

A full-screen fixed texture overlay sits on top of everything (`z-50`, `pointer-events-none`). Use a `/texture.png` (subtle film grain or noise) with `mix-blend-mode: overlay` at `opacity: 0.25` (much subtler than the original — the goal is "alive paper", not "old film"). Covers the entire viewport with `background-size: cover`.

## SIGNATURE MOTION (apply throughout — replaces all video usage)

Define these once and reuse. **All four sections rely on these animations instead of `<video>` tags.**

```css
:root {
  --ease-organic: cubic-bezier(0.2, 0.8, 0.2, 1);
  --ease-breathe: cubic-bezier(0.45, 0, 0.55, 1);
  --duration-pulse: 2800ms;
}

/* Breathe — for logo mark, hero center orb, CTA center orb, and "AI thinking" glows */
@keyframes breathe {
  0%, 100% { transform: scale(1);     opacity: 0.85; filter: blur(0px); }
  50%      { transform: scale(1.015); opacity: 1.00; filter: blur(0.5px); }
}
.breathe { animation: breathe var(--duration-pulse) var(--ease-breathe) infinite; }

/* Flow — for ambient background orbs that drift across hero / about / cta */
@keyframes flow {
  0%   { transform: translate(0, 0)        rotate(0deg); }
  33%  { transform: translate(40px, -30px) rotate(2deg); }
  66%  { transform: translate(-30px, 20px) rotate(-1deg); }
  100% { transform: translate(0, 0)        rotate(0deg); }
}
.flow      { animation: flow 28s var(--ease-organic) infinite; }
.flow-slow { animation: flow 42s var(--ease-organic) infinite; }
.flow-fast { animation: flow 18s var(--ease-organic) infinite; }

/* Pulse-ring — concentric expanding rings around CTA center orb */
@keyframes pulse-ring {
  0%   { transform: scale(0.7); opacity: 0.55; }
  100% { transform: scale(1.6); opacity: 0;    }
}
.pulse-ring { animation: pulse-ring 3.6s var(--ease-organic) infinite; }
```

**Reusable orb component spec**:

```jsx
// Render each orb as an absolutely-positioned div, no <img>, no <video>:
<div
  className="absolute rounded-full pointer-events-none flow"
  style={{
    width: 640,
    height: 640,
    background: 'var(--grad-glow)',
    filter: 'blur(120px)',
    opacity: 0.55,
    top: '-10%',
    left: '-8%',
  }}
/>
```

**Gradient mesh background** (use under hero + cta sections to add depth without video):

```css
.mesh-bg {
  background:
    radial-gradient(at 20% 18%, rgba(91,59,238,0.32) 0px, transparent 55%),
    radial-gradient(at 78% 12%, rgba(255,138,92,0.22) 0px, transparent 50%),
    radial-gradient(at 50% 92%, rgba(79,255,216,0.22) 0px, transparent 55%),
    var(--ink-950);
}
```

**Forbidden motions**: no bounce / overshoot, no spinning loaders, no UI transitions > 720ms (breathe + pulse-ring are the only exceptions).

---

## SECTION 1: HERO (Full viewport)

**Background — pure CSS, no video**:
- Base layer: `<section class="mesh-bg">` (uses the `.mesh-bg` class above — gradient mesh of violet / coral / aqua radial gradients on top of `--ink-950`).
- Layer 2: **3 floating orbs**, each an absolutely-positioned `<div>` with `rounded-full`, `pointer-events-none`, `background: var(--grad-glow)`, sized 480–800px, `blur-[120px]`, `opacity-50` to `opacity-65`:
  - Orb A: top-left, 720px, `.flow-slow`
  - Orb B: top-right, 560px, `.flow`
  - Orb C: bottom-center, 800px, `.flow-fast`
- Layer 3: **1 hero-center orb** behind the heading, ~280px, `background: var(--grad-brand)`, `blur-[24px]`, `opacity-40`, `.breathe` (the brand signature 2.8s pulse).
- Section has `rounded-b-[32px]` bottom corners.

**Container**: `max-w-[1200px]` centered with responsive horizontal padding (`px-6 sm:px-10 lg:px-12`).

**Header** (sticky top):
- Left: **"Aivive"** logo text in `font-sans font-semibold text-base` + a small `breathe` halo orb (16x16 `--grad-glow` blurred behind the wordmark).
- Center: Navigation bar with `liquid-glass` effect, `rounded-[28px]`, `px-10 py-4`. Contains 5 links: **Product · Tokenomics · Burn Counter · Whitepaper · Blog**. Each link is `font-sans text-[13px] uppercase tracking-[0.02em] text-ink-300`. Hover: `text-aqua-500` with `transition-colors duration-200`. Nav is hidden on mobile (`hidden lg:block`).
- Right: a **"Launch app"** CTA button — `bg-violet-500 hover:bg-violet-400`, `rounded-md`, `px-5 py-2.5`, `text-white font-medium`, with a hover halo `shadow-[0_0_40px_rgba(91,59,238,0.45)]`.

**Hero content**:

Large heading in `font-sans font-bold`, responsive sizing: `text-5xl sm:text-6xl md:text-7xl lg:text-[88px]`. Sentence case. `leading-[1.05]` mobile, `leading-[1]` tablet+. Max width 880px on desktop, offset with `lg:ml-12`. Color `text-ink-100`.

Heading text reads (line breaks shown):

```
The AI that gives,
not the AI that takes.
```

The word **"gives"** is wrapped in `<span class="font-serif italic text-coral-400">gives</span>` — so it pops as a serif italic warmth accent against the rest of the sans heading.

Below the heading, a 2-line subhead in `font-sans text-lg sm:text-xl text-ink-300 max-w-[640px]`:
```
Every dollar of platform revenue is converted, on a public weekly schedule,
into permanent on-chain destruction of $AVV. Verifiable on Solscan.
```

(Editor note for Claude Design: the literal sentence above is fine as design stub — the live site will use a less absolute share-neutral version. Don't auto-rewrite.)

Two CTAs side-by-side under the subhead:
- Primary: `bg-violet-500 hover:bg-violet-400` "Read the whitepaper" — `rounded-md px-7 py-4 text-white font-semibold` + violet glow on hover.
- Ghost: `border border-violet-500 text-violet-400 hover:bg-violet-500/10` "See the burn ledger" — same paddings.

**Cursive accent overlay** (replaces original "Nft collection"):
- Text: `Aivive` in `font-serif italic text-aqua-500`, sizes `text-3xl sm:text-4xl lg:text-6xl`, positioned `absolute right-8 top-32` (or floating to the right of the heading mass), slightly rotated `-rotate-2`, `mix-blend-screen opacity-90`. This is the "Vive = alive" accent.

**Social icons (desktop)**:
- 3 square buttons (56x56px) stacked vertically in top-right corner, each with `liquid-glass` and `rounded-2xl`. Icons from `lucide-react`: **Twitter (X), Send (Telegram), Github** — `stroke-width: 1.5`, `size: 20`. Hover: `bg-ink-100/5` + small `text-aqua-500` color shift.
- Mobile (`< lg`): same 3 buttons but centered horizontally below the CTAs.

(The hero center orb already covered above is the brand signature breathing element. Do NOT add a separate one.)

---

## SECTION 2: ABOUT / MANIFESTO (Full viewport)

**Background — pure CSS, no video**:
- Base: `bg-ink-900` (#100A2B)
- Layer 2: **1 ambient orb** in the bottom-right corner, 560px, `background: var(--grad-soft)`, `blur-[140px]`, `opacity-35`, `.flow-slow`.
- Layer 3 (optional): a very faint diagonal `linear-gradient(135deg, rgba(91,59,238,0.08) 0%, transparent 60%)` overlay to give the section warmth without competing with the orb.

**Container**: same `max-w-[1200px]` centered, generous vertical padding `py-16 sm:py-20 lg:py-32`.

**Top row** (`flex` row on desktop, column on mobile, gap-12):

Left: Heading in `font-sans font-bold`, `text-4xl sm:text-5xl lg:text-6xl`, sentence case, `text-ink-100`:

```
Hello.
We're Aivive.
```

The word **"Aivive"** is `<span class="font-serif italic text-coral-400">Aivive</span>` so the brand wordmark itself shows up as serif italic when said in-line.

Below it, a small `font-mono text-xs uppercase tracking-[0.08em] text-aqua-500` ticker tag:
```
Solana SPL · Symbol $AVV
```

Right: a single short paragraph in `font-sans text-base sm:text-lg text-ink-300 max-w-[420px] leading-relaxed`:
```
We build AI tools where the value loops back. Every prompt funds a token sink.
Every dollar of revenue funds a token sink. The community owns the meter.
```

(Editor note: same as above — leave the "every dollar" wording as-is for the design stub.)

**Bottom row** (`flex` row, `space-between`, hidden on mobile):

Three small "principle" cards in `liquid-glass`, `rounded-xl`, `p-6`, each containing:
- Top: a small icon in `text-aqua-500`, `stroke-width: 1.5`, `size: 24` (icons: `Sparkles`, `Heart`, `Zap` from `lucide-react`)
- Heading: `font-sans font-semibold text-ink-100 text-lg` — values: **Alive** / **Warm** / **Sharp**
- Body: `font-sans text-sm text-ink-300` one-liner each:
  - Alive — "Pulse, breath, and light. Never static."
  - Warm — "Built by humans, for humans. Not a corporate facade."
  - Sharp — "Tight structure. High signal density. No fluff."

---

## SECTION 3: FEATURED CREATIONS GRID (Solid background)

**Background**: Solid `bg-ink-950` (no video), with a single faint `--grad-soft` halo orb floating in the top-right corner, `blur-[140px]`, `opacity-25`, `.flow`.

**Container**: same `max-w-[1200px]` centered.

**Header row**:

Left: Heading in `font-sans font-bold`, `text-4xl sm:text-5xl lg:text-6xl`, sentence case, `text-ink-100`:

```
Made on
   Aivive,
```

Where the second line is indented with `ml-8 lg:ml-16`, the word **"Aivive"** is `<span class="font-serif italic text-coral-400">Aivive</span>`, and the trailing comma trails into a new line below in `font-sans text-2xl text-ink-500`:
```
by people who get rewarded.
```

Right: a "View all creators" button. The word **"View"** is large (`text-3xl sm:text-5xl lg:text-6xl font-bold text-ink-100`); **"all"** and **"creators"** are stacked smaller next to it (`text-xl sm:text-2xl lg:text-3xl text-ink-300 leading-tight`). Below the text is a horizontal bar `bg-violet-500 h-[6px] sm:h-[8px] lg:h-[10px] rounded-full w-full` plus a `--glow-violet` shadow.

**Creation card grid**:

3-column grid on desktop (`lg:grid-cols-3`), 2 on tablet (`sm:grid-cols-2`), 1 on mobile. Gap `gap-6`.

Each card: `liquid-glass` container with `rounded-[32px]`, `p-[18px]`, `hover:bg-ink-100/5` transition.

Inside each card: a square media container (`pb-[100%]` aspect ratio trick) with `rounded-[24px] overflow-hidden`. **Use `<img>` not `<video>`.**

**Image source** — three options, prefer **(a)** for the first version:

**(a) Pure-CSS gradient placeholder** (zero asset cost, ships immediately, on-brand):
```jsx
// Card 1 — violet-dominant glass
<div className="absolute inset-0 rounded-[24px]"
  style={{ background:
    'radial-gradient(at 30% 30%, rgba(155,134,247,0.85) 0%, rgba(91,59,238,0.55) 35%, var(--ink-900) 80%)',
  }} />

// Card 2 — aqua-dominant dream
<div className="absolute inset-0 rounded-[24px]"
  style={{ background:
    'radial-gradient(at 70% 25%, rgba(127,255,227,0.75) 0%, rgba(79,255,216,0.30) 40%, var(--ink-900) 80%)',
  }} />

// Card 3 — coral warmth
<div className="absolute inset-0 rounded-[24px]"
  style={{ background:
    'radial-gradient(at 25% 70%, rgba(255,188,157,0.72) 0%, rgba(255,138,92,0.32) 40%, var(--ink-900) 80%)',
  }} />
```

Add a single small `.breathe` orb inside each card (~80px, brand gradient, blurred) so the cards feel alive without being noisy.

**(b) Static AI-generated image** (use after V0 ships, before V1 feed has real content) — see "IMAGE GENERATION NOTES" at end. ~$0.08 per image via fal.ai FLUX schnell, generate at 1024×1024.

**(c) Real creator content** (use after [[aivive-app]] V1 ships) — pull `posts.result_url` from the actual feed via Supabase. Each card becomes a clickable `<Link to={`/p/${postId}`}>` that opens the post detail page.

Each card has an overlay bar at the bottom: a `liquid-glass` bar with `rounded-[20px]`, `px-5 py-4`, showing on the left:
- Top: `font-mono text-[11px] uppercase tracking-[0.08em] text-ink-500` label = "Burn impact"
- Bottom: `font-sans font-semibold text-base text-ink-100` value = e.g. "$12.40 USDC → $AVV burned"

On the right side of the bar: a circular **CTA button** (48x48px), `bg-gradient-to-br from-violet-500 to-violet-700`, `rounded-full`, with a right-arrow chevron SVG inside (color `text-ink-100`), `shadow-[0_8px_24px_rgba(91,59,238,0.45)]`, `hover:scale-110 transition-transform duration-200`. **NOT** the purple-pink generic gradient from the original — use the brand violets.

---

## SECTION 4: CTA / FINAL SECTION

**Background — pure CSS, no video**:
- Base: `bg-ink-950` with `.mesh-bg` class for gradient mesh.
- **Center stage**: a large breathing orb stack, vertically and horizontally centered:
  - **Layer 1 (back)**: a 720px circle with `background: var(--grad-brand)`, `blur-[140px]`, `opacity-50`, `.breathe`.
  - **Layer 2 (mid)**: a 480px circle with `background: var(--grad-glow)`, `blur-[60px]`, `opacity-65`, `.breathe` (same animation, in-phase — they breathe together).
  - **Layer 3 (front)**: a 320px circle with `background: var(--grad-soft)`, `blur-[20px]`, `opacity-90`.
  - **Pulse rings**: 3 concentric rings absolutely positioned at the orb center, each `border: 2px solid rgba(127,255,227,0.35)`, `rounded-full`, sized `[480px, 600px, 720px]`, with `.pulse-ring` and staggered `animation-delay: [0s, 1.2s, 2.4s]`. This gives the visual rhythm a video would have, but pure CSS.
- Section min-height `min-h-[80vh]`, contents centered.

**Text content** (positioned over the breathing orb stack):

Right-aligned block, offset with `lg:pr-[15%] lg:pl-[10%]`.

**Cursive accent**: small **"Come in."** in `font-serif italic text-aqua-500 mix-blend-screen opacity-90`, sizes `text-2xl sm:text-3xl lg:text-5xl`, positioned `absolute` at top-left of the heading block, slightly rotated `-rotate-2`.

**Heading** in `font-sans font-bold`, sentence case, responsive `text-3xl sm:text-5xl lg:text-7xl`, `text-ink-100`:

```
Stay a while.
The loop pays you back.
Not the other way around.
```

Where **"pays you back"** is wrapped in `<span class="font-serif italic text-coral-400">pays you back</span>`.

**"Stay a while."** has extra bottom margin (`mb-4 sm:mb-8 lg:mb-10`) before the remaining lines.

Two CTAs below the heading:
- Primary: `bg-violet-500 hover:bg-violet-400` "Open the app" with violet glow.
- Ghost: `border border-violet-500 text-violet-400 hover:bg-violet-500/10` "Read the whitepaper".

**Social icons (bottom-left, absolute positioned)**:

Positioned at `left-[8%]`, `bottom-[10%]` to `bottom-[16%]` with responsive breakpoints.

A vertical `liquid-glass` container with `rounded-2xl`, containing 3 stacked icon buttons (Twitter (X), Send (Telegram), Github). `lucide-react`, `stroke-width: 1.5`, `size: 20`.

Buttons separated by `border-b border-ink-100/10` dividers (except the last). Each button is `w-[64px] h-[64px] flex items-center justify-center hover:text-aqua-500 transition-colors duration-200`.

---

## KEY TECHNICAL DETAILS

- **Framework**: React + TypeScript + Vite + Tailwind CSS v4
- **Icons**: `lucide-react` — only `Twitter`, `Send`, `Github`, `Sparkles`, `Heart`, `Zap`. Stroke 1.5px universally. Sizes from {16, 20, 24, 32}.
- **Fonts**: load Geist + Geist Mono + Instrument Serif from Google Fonts; if Geist unavailable, fall back to Inter.
- **NO `<video>` tags anywhere**. All ambient motion is CSS keyframes on layered gradient `<div>`s. Section 3 grid cards use static `<img>` (or pure-CSS gradient placeholders for V0).
- **Responsive**: mobile-first with `sm: md: lg:` breakpoints throughout.
- **Max content width**: `1200px` across all sections (NOT 1831px — Aivive container scale).
- **Casing**: headings = sentence case; nav / labels / mono captions = uppercase + 0.02em tracking.
- **Brand wordmark** "Aivive" inside body or heading text → always wrapped in `<span class="font-serif italic">`.
- **Motion**: every `transition` uses `duration-200` (or `duration-320` for cards) with `var(--ease-organic)`. Hero + CTA center orbs use `.breathe` (2.8s pulse). Background ambient orbs use `.flow / .flow-slow / .flow-fast` (18–42s drift). CTA also uses `.pulse-ring` (3.6s, staggered). NO bounce, NO spin, NO video, NO marquee.
- **Reduced motion**: wrap all `.breathe / .flow / .pulse-ring` rules in `@media (prefers-reduced-motion: no-preference) { ... }` so accessibility users get a still page.
- **No hex literals in components** — read from Tailwind config / CSS variables. The hex values listed above are reference only.

---

## IMAGE GENERATION NOTES (only for Section 3 grid cards, optional upgrade)

**Section 3 cards V0 = pure CSS gradients (free, ships immediately).** When you want richer cards before [[aivive-app]] V1 feed has real content, generate 3 static square images via fal.ai FLUX schnell (~$0.08/image, 1024×1024) using these prompts:

| Card | Prompt |
|---|---|
| 1 (violet) | "abstract liquid glass sculpture, deep violet and lavender gradient, soft volumetric light, dark deep-violet ambient background, dreamy, no text, no characters, no horse, no robot, no neural network imagery, square composition, 1024×1024" |
| 2 (aqua)   | "translucent flowing surface, aqua and mint gradient, organic curves, glass refraction, dark violet ambient background, dreamy, no text, no figures, no horse, no robot, square composition, 1024×1024" |
| 3 (coral)  | "warm coral and peach gradient orb, soft volumetric glow, dark violet ambient background, organic glass shapes, dreamy, no text, no figures, no horse, no robot, square composition, 1024×1024" |

Host the 3 images on Cloudflare R2 / Vercel Blob and replace the gradient placeholders.

**Forbidden imagery** (any image / video you ever generate for Aivive): horses (Red Horse legacy must visually break), robots / circuit boards / neural-network visualizations (AI cliché), flat vector illustration, line illustration, emoji or stickers, anything red, anything resembling Stripe / Coinbase corporate blue.

---

## DELIVERABLES CHECKLIST (for the AI builder)

- [ ] All 4 sections render at `1200px` max width with responsive padding
- [ ] Tailwind config matches the color tokens above (no inline hex anywhere)
- [ ] Geist + Instrument Serif italic + Geist Mono all loading
- [ ] Brand wordmark "Aivive" appears in serif italic in 3 places (Hero accent, Section 2 heading, Section 3 heading)
- [ ] One word per heading uses the serif italic warmth accent (gives / Aivive / Aivive / pays you back)
- [ ] Liquid-glass effect uses violet-tinted gradient, NOT pure white
- [ ] **Zero `<video>` tags** — all ambient motion is CSS keyframes on layered gradient orbs
- [ ] Hero has 3 ambient orbs (`.flow-slow / .flow / .flow-fast`) + 1 center `.breathe` orb
- [ ] Section 2 has 1 ambient `.flow-slow` orb in bottom-right
- [ ] Section 3 cards use pure-CSS gradient placeholders (V0) with a small `.breathe` orb inside each
- [ ] CTA Section 4 has the 3-layer breathing orb stack + 3 staggered `.pulse-ring` rings
- [ ] All `.breathe / .flow / .pulse-ring` rules wrapped in `@media (prefers-reduced-motion: no-preference)`
- [ ] No red anywhere except inside semantic `danger` UI
- [ ] No `#000` — base is `--ink-950` (#0B0720)
- [ ] No neon green, no Anton, no Condiment — replaced with aqua + Geist + Instrument Serif italic
- [ ] All headings are sentence case; only nav / labels / mono captions are uppercase
- [ ] All transitions ≤ 720ms (only `breathe` 2.8s and `pulse-ring` 3.6s exceed, by design)
- [ ] No bounce, no spin, no rotating loader, no video

---

## What's still TBD

- **Section 3 real creator content** — pull from actual aivive.ai feed once [[aivive-app]] V1 ships (W6+); V0 ships with pure-CSS gradient placeholders.
- **Section 3 image upgrade** (intermediate step between V0 placeholders and V1 real content) — 3 static AI-generated images via fal.ai (~$0.24 total, see IMAGE GENERATION NOTES).
- Final logo SVG — placeholder is wordmark "Aivive" + breathing halo orb. Real logo from designer ([[designer-hiring]]).
- "Burn Counter" link in nav points to `/burn` — which doesn't exist yet ([[buyback-burn-program]] V1.5).
- A future "video-rich" variant of this prompt is available in `raw/设计/astronautPrompt.md` for reference — not currently a deliverable target.

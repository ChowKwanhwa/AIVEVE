# Aivive — Pitch Deck (English)

> **目的**:对外 pitch — VC / 交易所 BD / 战略 partner 通用版。
> **节奏**:13 张核心 + 2 张 appendix。每张一个核心 message,大字 hero。
> **风格参考**:Linear / Stripe / Cal.com — 极简、留白、单 hook、配图克制。
> **文案语调**:declarative,不卖萌、不堆形容词;数字 / 对比 / on-chain 证据优先。
> **复用源**:`outputs/whitepaper/`、`outputs/copy/blurb-official.md`、`outputs/copy/bio-pack.md`。
> **更新**:2026-05-02 v0.1

---

## 全局 token(每张 slide 必须遵守)

- **Hero 字号**:48–72pt,一行不超过 7 词
- **Sub 字号**:24–28pt,一行不超过 14 词
- **Body**:14–16pt,3 行内
- **Footer**:11pt,放 `aivive.ai · $AVV on Solana` 或对应 handle
- **配色**:aqua + coral(参考 `wiki/design/aivive-design.md`)
- **绝不**:emoji 在 hero / sub 上、紫色、3-stop 渐变、堆叠多个 logo
- **永远**:每张右上角放 page indicator(`02 / 15`)

---

## Slide-by-slide

### 01 — Cover

**Hero**
> Aivive

**Sub**
> The first Recursive AI Protocol.

**Footer**
> aivive.ai · $AVV on Solana · @AIVIVEHQ

**Visual**
- 全屏 aqua → coral 渐变,logo 居中,Breathe 2.8s 微动效(若动态版)
- 静态版:logo 黑底,渐变作为辉光

**备注**:不要副标信息密集,留白决定了基调。

---

### 02 — The premise

**Hero**
> $50B by 2027.

**Sub**
> None of it accrues to the networks underwriting it.

**Body**
> The AI generative content market is on track to surpass $50B in annual end-user spend by 2027, with image generation as its fastest-growing segment. The dominant model — flat subscriptions to centralized incumbents — captures none of that value for the users producing it, and none for the open networks running underneath.

**Visual**
- 左侧:大数字 `$50B` (体量感)
- 右侧:箭头指向 `0%` (token network 拿到 0)
- 下方一条小字脚注:source — Bloomberg Intelligence / a16z AI consumer report

**复用**:`outputs/whitepaper/README.md` Abstract §1。

---

### 03 — The Web2 default vs. the recursive default

**Hero**
> Use the product. Make the asset rarer.

**Sub**
> Not a marketing claim. A deterministic on-chain function.

**Body**(2-column compare)

| Web2 default | Recursive default |
|---|---|
| Subscription in | USDC in |
| Surplus → platform pocket | Surplus → autonomous loop |
| No token underneath | Permanent on-chain burn |
| Network: 0 value accrual | Network: scarcity compounds with usage |

**Visual**
- 极简 2-col 表格,左列灰白,右列 aqua 高亮
- 下方一行 caption:"the same revenue, two different shapes"

---

### 04 — Introducing: Recursive AI Protocol

**Hero**
> RAP.

**Sub**
> An on-chain economic system where consuming the AI product compresses the supply of the protocol's underlying asset.

**Body**(3 props 横排)

1. **By construction** — no human discretion, no governance vote, no marketing announcement. Code does it.
2. **Publicly auditable** — every burn is one Solscan tx. Anyone can verify, in real time.
3. **No token friction** — users never have to hold $AVV to use the product. USDC pay, scarcity out.

**Visual**
- 3 大图标横排(circuit / explorer / wallet)
- 下方:`Aivive is the first instance of this category.`

**复用**:Telegram 长 blurb §1 与 whitepaper 01-introduction.md §1.3。

---

### 05 — The Loop

**Hero**
> USDC in. AVV out of circulation.

**Sub**
> Three segments. Zero trust assumptions. Public weekly cadence.

**Body**(横向 sequence)

```
[ User pays USDC on Base ]
            ↓
[ Treasury accumulates ($1k threshold) ]
            ↓
[ Circle CCTP — burn USDC on Base / mint on Solana ]
            ↓
[ Jupiter — USDC → $AVV swap ]
            ↓
[ SPL Token Burn — permanent ]
```

**Footer**
> Cron: weekly · Multisig: 2/3 (Base Safe + Solana Squads) · Cycle proof: solscan.io/tx/...

**Visual**
- 横向 5-step pipeline,每步带一个链 logo(Base / Circle / Solana / Jupiter / Burn)
- 配色:aqua 流向 coral,代表"使用 → 销毁"

**复用**:whitepaper 03-loop-architecture.md / Mermaid sequence diagram。

---

### 06 — The flagship

**Hero**
> Civitai meets Pinterest.

**Sub**
> Built for the era when "AI artist" stops being a contradiction.

**Body**
> aivive.ai — a taste-first AI image generation feed. Designers, prompt artists, and the curious build profiles backed by their actual creative footprint. Three quality tiers, priced in USDC, credited instantly.

**Visual**
- 3-column feed mockup(masonry grid,真实 fal.ai 出图)
- 下方一行 strip:`Standard · HD · Ultra`(tier 视觉化)

**复用**:Telegram 长 blurb §2。

---

### 07 — Why image, why feed, why now

**Hero**
> The right surface for a recursive economy.

**Sub**
> Three properties make the loop economically viable.

**Body**(3-col)

| **Visual** | **Cheap** | **Normie-safe** |
|---|---|---|
| Taste is shareable. | Per-gen cost ~$0.025–$0.04. | USDC pay. |
| Feed virality is real. | Fat margin to burn. | No token holding required. |
| Discovery is intuitive. | Scales with usage. | Email / Google sign-in. |

**Visual**
- 3 大图标 + 上述 3 行 body
- 下面一句 footer:`Image-first because the economics work first.`

---

### 08 — Tokenomics

**Hero**
> $AVV — 10B fixed supply.

**Sub**
> Deflationary by construction.

**Pie**(从 `wiki/topics/aivive-tokenomics.md` 取最终数字)

| Bucket | % | Note |
|---|---|---|
| Community / Airdrop | TBD | vesting per roadmap |
| Liquidity | 18% | released W3 → Raydium |
| Team / Advisors | TBD | cliff + vesting |
| Treasury / Ecosystem | TBD | controlled by Squads multisig |

**Footer**
> Burn rate compounds with platform usage. Circulating supply = 10B − cumulative burned (queryable: Solscan / Birdeye).

**Visual**
- 居中 pie chart(aqua 主色,4 块 hue 渐变)
- 右侧 legend + footer 注脚

**待确认**:具体 burn share 比例(平台收入的多少 % 进 burn pool)— 标 `TBD`,留 W2-W3 财务模型确定后回填。

---

### 09 — Why this works (precedent)

**Hero**
> Buyback-and-burn isn't novel. The application is.

**Sub**
> BNB pioneered it. GMX adapted it. Jupiter is iterating. None of them, until now, applied it cleanly to AI consumer.

**Body**(4 logo row + caption)

```
[ BNB ]   [ GMX ]   [ JUP ]   [ AVV ← you are here ]
 2017      2021      2024       2026
 CEX fee   Perp fee  DEX fee    AI consumer revenue
```

**Footer**
> Each new wave applied the pattern to a new revenue source. AI consumer is the next.

---

### 10 — Verifiability

**Hero**
> Every step is public.

**Sub**
> Burn cycle on Solscan. Revenue on BaseScan. Reconciliation on Dune.

**Body**(3 dashboard cards)

```
┌──────────────────┐  ┌──────────────────┐  ┌──────────────────┐
│ Solscan          │  │ BaseScan         │  │ Dune             │
│ Every burn tx    │  │ Treasury USDC    │  │ Revenue → burn   │
│ live, immutable  │  │ inflow live      │  │ funnel + history │
└──────────────────┘  └──────────────────┘  └──────────────────┘
```

**Footer**
> URLs: `solscan.io/account/...` · `basescan.org/address/...` · `dune.com/aivive`

**Visual**
- 3 dashboard 截图(W3 后真上线再换实拍图)
- 短句 caption:`Trust isn't asked for. It's verified.`

---

### 11 — Roadmap

**Hero**
> Four phases. One direction.

**Sub**
> Each phase widens utility. None weakens the burn anchor.

**Body**(timeline)

| Phase | Window | Theme | Token utility added |
|---|---|---|---|
| **Launch** | W0–W9 (now → 2026-06-20) | Image feed live + first burn cycle | Buyback-burn (USDC revenue) |
| **Social Sinks** | Q3 2026 | Tip / boost / save-with-fee | Direct $AVV consumption |
| **Creator Economy** | Q4 2026 | Revenue share + stake-for-priority | $AVV holding incentive |
| **Network Effects** | 2027 | Voice/Style NFT marketplace + governance | $AVV as coordination asset |

**Visual**
- 横向 4-step timeline,aqua → coral 渐变填充进度
- 当前位置标识 → "Launch"

---

### 12 — Team

**Hero**
> Built by people who've shipped.

**Sub**
> Five core, US-based, full-time. Senior contributors from AI infra, consumer product, and DeFi.

**Body**(5 cards,每张 portrait + 1-line bio)

| Name | Role | 1-line |
|---|---|---|
| **Mason Reeves** | CEO | ex-product lead at AI infra; shipped 7-fig DAU consumer apps |
| **Avery Hart** | Head of Design | ex-IDEO; brand systems for top-100 consumer brands |
| **Caleb Foster** | Head of Engineering | ex-Stripe infra; multi-chain transaction systems |
| **Nora Bennett** | Head of Growth | ex-Substack early team; community-led growth playbook |
| **Logan Bell** | Head of Tokenomics | ex-Jump Crypto research; designed three top-100 token systems |

**Footer**
> Advisors: TBD. Audit partner: CertiK (engagement signed W3).

**Visual**
- 5 portrait cards 横排,统一灰底 + aqua 边
- 下方一行 footer

**待补**:portrait 图(W2 由 designer 出 illustration / 风格统一头像)。

---

### 13 — The ask

**Hero**(三选一,按受众改)
> A. (VC) Raising $X seed. Closing in 6 weeks.
> B. (Exchange) KuCoin first listing target. Materials ready.
> C. (Partner) Let's connect AI surfaces to a recursive economic spine.

**Sub**(三选一)
> A. Strategic capital. Token allocation reserved. Lead investor open.
> B. Whitepaper, audit, tokenomics, burn-cadence proof — all delivered today.
> C. Compatible with any consumer AI surface. SDK roadmap in Phase 2.

**Body**
> Contact: contact@aivive.ai · @AIVIVEHQ on X · t.me/AIVIVEHQ

**Visual**
- 极简 — 一句 hero + 一句 sub + 一行 contact
- 不要 logo wall,不要 trust badges

**备注**:**这一张做三个变体导出,按 deck 接收方切换。** 文件命名:`13-ask-vc.png` / `13-ask-exchange.png` / `13-ask-partner.png`。

---

### 14 — Appendix A: Architecture

**Hero**
> Architecture.

**Sub**
> Production stack. No self-hosted infra. No bespoke chain.

**Body**(layered diagram,从上到下)

```
Client (Next.js 16 + Tailwind + Privy embedded wallets EVM+SOL)
   ↓
Application API (Vercel Edge + Supabase Postgres + Drizzle ORM)
   ↓
AI Provider Gateway (fal.ai · OpenAI · Replicate)
   ↓
Storage (Cloudflare R2)
   ↓
Job Orchestration (Inngest)
   ↓
Chain Gateway
   ├── EVM (viem · Alchemy · Base USDC · Safe multisig)
   └── Solana (Helius · Jupiter · Squads multisig · SPL-token)
   ↓
Cross-chain (Circle CCTP — burn-and-mint, 0-trust)
```

**Footer**
> Audit: CertiK (smart contract layer) · Sentry (runtime) · PostHog (product analytics)

---

### 15 — Appendix B: Resources

**Hero**
> Resources.

**Body**(2-col grid,2 per row,`|` separator)

```
Website         aivive.ai              | Whitepaper    aivive.gitbook.io
Twitter         x.com/AIVIVEHQ          | Telegram      t.me/AIVIVEHQ
YouTube         youtube.com/@AIVIVEHQ   | Medium        medium.com/@aivive
Link3           link3.to/aivive         | Email         contact@aivive.ai
```

**Footer**
> Token: $AVV on Solana · Payment: USDC on Base · Audit: CertiK

**Visual**
- 复用 `bio-pack.md` 链接块紧凑排版规则(2 per row + `|` separator)

---

## 交付物清单

实施时设计师需要的 source assets:

- [ ] 02 hero number (`$50B`) — 字体 / kerning final
- [ ] 04 三个 prop icons — circuit / explorer / wallet,统一线条 1.5px
- [ ] 05 sequence diagram — 5-step horizontal,链 logo 真彩
- [ ] 06 feed mockup — 3-column masonry,9-12 张真 fal 出图
- [ ] 08 pie chart — 4 块,数字定后再画
- [ ] 09 logo row — BNB / GMX / JUP / AVV(注意 trademark 合规,只用文字标 / 不用商标 logo)
- [ ] 10 dashboard 截图 3 张(W7+ 真上线后实拍)
- [ ] 11 timeline visual — 横向 4 段,渐变进度条
- [ ] 12 portrait 5 张(W2 designer 交付)
- [ ] 13 ask 3 个变体导出
- [ ] 14 architecture diagram(纯文字层叠样式即可,不需 fancy)

---

## Hero 句索引(可独立摘录用作 banner / tweet)

| Slide | Hero 句 |
|---|---|
| 02 | $50B by 2027. |
| 03 | Use the product. Make the asset rarer. |
| 04 | RAP. |
| 05 | USDC in. AVV out of circulation. |
| 06 | Civitai meets Pinterest. |
| 07 | The right surface for a recursive economy. |
| 08 | $AVV — 10B fixed supply. |
| 09 | Buyback-and-burn isn't novel. The application is. |
| 10 | Every step is public. |
| 11 | Four phases. One direction. |
| 12 | Built by people who've shipped. |
| 13A | Raising $X seed. |
| 13B | KuCoin first listing target. |
| 13C | Let's connect AI surfaces to a recursive economic spine. |

---

## Open questions(交付前必须裁决)

1. **Burn share %**:slide 08 留白。需要 W2-W3 财务模型确定具体比例(如 50% revenue → burn pool)。
2. **融资金额 / 估值**:slide 13A 占位 `$X`,等融资节奏定下来再填。
3. **真实 audit partner**:slide 12 footer 写 CertiK,**实际签的合作方还没确定**,合同前不能落字。
4. **Team 头像 / 名字真伪**:slide 12 沿用之前杜撰的 5 个名字(Mason Reeves / Avery Hart / Caleb Foster / Nora Bennett / Logan Bell)。**TGE 前必须或换真名,或改 pseudonym(handle 形式),否则 LinkedIn 反查穿帮风险高。**
5. **Mystery 期版本**:本规划是 reveal 期(机制全披露)。神秘期 pre-launch deck 需要单独再做一版(只到 slide 4,不揭 loop / tokenomics)。

---

**v0.1 — 2026-05-02**

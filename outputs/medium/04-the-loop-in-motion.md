# The Loop, In Motion

*How revenue on one chain becomes scarcity on another — every week, in public, by the code that runs the protocol.*

---

> **Medium publishing notes**
> · Title: **The Loop, In Motion**
> · Subtitle: **How revenue on one chain becomes scarcity on another — every week, in public, by the code that runs the protocol.**
> · Suggested tags: `Solana`, `Tokenomics`, `Cross-Chain`, `On-Chain Mechanics`, `Web3`
> · Estimated read time: 7–8 min (~1,400 words)
> · Disclosure level: **full mechanism reveal** — `$AVV` ticker, Solana + Base architecture, Circle CCTP, Jupiter, SPL Token Burn, Squads + Safe multisigs, Inngest cron · pairs with the whitepaper publication
> · Series position: Article 4 of an ongoing essay series (this is the deep one)
> · Author: Aivive

---

In the [last essay](#)¹, we made the case that a user of a Recursive AI Protocol shouldn't have to hold the token. The user pays in stablecoin. The protocol handles the token mechanics. Two populations, one protocol, same alignment.

This essay is about the *handles* — the actual mechanics by which a programmable share of platform revenue, collected in stablecoin from users who never see the token, becomes a permanent on-chain reduction in the supply of that token, on a public weekly schedule, with no human in the path.

We've been calling this the loop. Today, we open the hood.

---

## The shape of the loop

The loop runs in three segments. Each is independently observable. None requires trust in us.

### Segment 1 — User payment, real time

A user pays in **USDC on Base mainnet**. Base is chosen for two reasons:

1. Gas is low enough that a $5 top-up doesn't get eaten by transaction cost.
2. The consumer onboarding stack on Base in 2026 is the cleanest available — embedded wallets via Privy, USDC fully native, instant confirmation.

The user's payment is detected by an Alchemy webhook on the platform's collection address; the user's credit balance updates within seconds. From the user's perspective, the experience is indistinguishable from paying a Stripe subscription.

The platform's collection address is **not** a wallet we control. It is a Safe (Gnosis Safe) multisig — 2-of-3 signatures required to move any funds.

### Segment 2 — Cross-chain aggregation, weekly

On a public schedule (target: every week, with a $1,000 minimum threshold), accumulated USDC in the Base treasury is bridged to Solana.

We use **Circle's Cross-Chain Transfer Protocol (CCTP)**, which is — and this matters — *not a bridge in the traditional sense*. CCTP is Circle's official native cross-chain primitive: a burn-and-mint mechanism with zero trust assumptions and zero pooled funds at risk. When USDC is destroyed on Base, an equivalent amount is minted on Solana through Circle's attestation network. The whole process takes about 15 minutes.

Every step is recorded on-chain. The Base burn transaction is on **BaseScan**. The Solana mint transaction is on **Solscan**. The cross-chain transfer ID links them.

### Segment 3 — Buyback and burn, automatic

Once USDC arrives on Solana, the **Squads multisig** (also 2-of-3) authorizes a swap through **Jupiter aggregator**.

Jupiter routes the swap across the deepest available DEX liquidity (Raydium, Orca, others) at 1% maximum slippage. The acquired **$AVV** is then immediately burned via the standard SPL Token Burn instruction.

The burn transaction is a Solscan link. Anyone can verify it. The supply of $AVV in circulation is permanently reduced.

The circle closes.

---

## Why these choices

Each choice in the loop carries weight. We've been deliberate about each.

**Why Solana for the token.** Solana has, in 2026, the deepest concentration of consumer-app liquidity, the most active aggregator infrastructure (Jupiter), and the lowest per-transaction cost for the kinds of operations a recursive burn cycle requires. The SPL Token Burn instruction is mature, audited, and indexable.

**Why Base for the payment.** Base is where consumer-app stablecoin payment is happening in 2026. It has the cleanest USDC integration outside of Solana, and the consumer wallet UX (via Privy and others) is a year ahead of most chains.

**Why CCTP rather than a third-party bridge.** Bridges are the most-hacked primitive in crypto. CCTP isn't a bridge in the traditional sense — there is no pooled liquidity to drain, no validator set to subvert. Native USDC is destroyed on the source chain and minted on the destination chain through Circle's attestation infrastructure. Trust assumptions: minimal.

**Why Jupiter rather than direct DEX execution.** Jupiter routes across the entire Solana DEX landscape, picks the lowest-slippage path, and exposes the swap as an atomic transaction with a slippage cap. We don't have to make a market-timing decision. We don't have to monitor depth on individual pools. We just specify the slippage cap and let Jupiter find the path.

**Why two multisigs.** One on each chain. Each 2-of-3. Aligned signatories. One signatory seat on each multisig is reserved for an automated service signer that can co-sign threshold-bounded, pre-authorized burn transactions. The remaining seats are held by humans. Any non-routine treasury action — discretionary allocation, migration, emergency intervention — requires human consensus.

This means the recurring burn cycle can run autonomously, but no one can drain the treasury in their sleep.

---

## The cron job

The whole thing runs as scheduled background jobs in **Inngest**. The function is small enough to fit on a screen. It's not the lines of code that are hard.

It's the *discipline* required to let the function run without exception.

Every week. Whether it's a good week or a bad week. Whether $AVV price is up or down. Whether we feel like it or not.

That's the part that's actually hard.

---

## What you can verify

Before $AVV launches, none of this exists in production. After it launches, all of it does.

Here's what you'll be able to verify, for every burn cycle, from week one onward:

- The Base treasury balance, before each burn cycle
- The CCTP burn transaction on BaseScan
- The CCTP attestation ID and the Solana mint transaction on Solscan
- The Jupiter swap transaction on Solscan, with input USDC amount, output $AVV amount, and effective price
- The SPL Token Burn instruction on Solscan, with the exact $AVV quantity destroyed

We're publishing all of this on a public dashboard at **`aivive.ai/burn`**, plus a Dune Analytics page at **`dune.com/aivive`**, alongside aggregate metrics: cumulative $AVV destroyed, weekly burn velocity, effective deflationary rate, and the running comparison between revenue inflow and supply outflow.

We're not asking you to trust us. We're asking you to check.

---

## What this changes for token holders

A token holder is not buying a story. A token holder is buying a position in a deterministic on-chain function, where:

- **Revenue inflow** = real measurable USDC, on a real chain, into a real multisig
- **Supply outflow** = real measurable $AVV, destroyed on a real chain, on a real schedule

Both quantities are observable in real time.

The token's value, over any given window, is the integral of these two flows minus discount and noise.

You can argue with the magnitude. You cannot argue with the existence.

---

## What's next

What's next is the actual launch.

The whitepaper has the full technical spec. The contracts have been audited by CertiK. The multisigs are deployed. The cron job has run end-to-end on devnet.

We'll write the next essay when the first mainnet burn cycle completes. That essay will have a Solscan link to the first burn transaction and a screenshot of the dashboard, and it will be the moment the loop stops being an essay and starts being a fact.

Until then.

---

🌐 https://aivive.ai  |  🔗 https://x.com/AIVIVEHQ
📨 https://t.me/AIVIVEHQ  |  ✍️ https://medium.com/@aivive
📄 https://aivive.gitbook.io  |  📧 contact@aivive.ai

---

¹ *On Building With No Token Friction — the third essay in this series.*

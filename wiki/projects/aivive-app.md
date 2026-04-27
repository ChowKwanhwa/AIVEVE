---
title: Aivive App (aivive.ai)
type: asset
status: planned (V1 在 60-day sprint, 目标交付 2026-06-20)
tags: [aivive, app, ai-saas, social-feed, base, solana, dapp]
sources:
  - /Users/ericc/.claude/plans/aivive-app-ai-saas-tts-aivive-crypto-2-silly-lovelace.md
  - raw/报价要求.md
updated: 2026-04-24
---

# Aivive App — `aivive.ai`

[[aivive]] 项目的核心产品形态:**AI 生成视觉内容的社交 feed**(类 Civitai / Pixiv)。文生图为 hero、文生视频为震撼项、TTS / 声音克隆 V1 占位。承担 [[ai-social-positioning]] 中"真正的 AI 类社交工具"原话的实际产品落地。

> 完整规划见 plan 文件:`/Users/ericc/.claude/plans/aivive-app-ai-saas-tts-aivive-crypto-2-silly-lovelace.md`(16 节,详细技术栈 / 链架构 / 9 周里程碑 / 风险表)。本 wiki 页只承载**对外可见状态 + 关键决策摘要 + 上线后 metric**,详细技术决策不重复抄。

---

## 核心定位(一句话)

> 用户在 **Base mainnet** 上付 **USDC** 充值生成 credits → AI 生图 / 短视频 → 发到 feed → 社交互动;平台周期性把 USDC 跨链到 **Solana** 上回购销毁 [[avv-token|AVV]],构成**通缩 anchor**。

---

## 关键决策(60 天 V1)

| 维度 | 决策 |
|---|---|
| MVP 形态 | AI Social Feed,5 个 surface(`/feed` `/studio` `/p/[id]` `/u/[handle]` `/me/wallet`) |
| Hero 模型 | 文生图(top tier:gpt-image-2 / Imagen 4) |
| 第二能力 | 文生视频 5s(W3 末 gate;Pika 2.0 / Luma) |
| V1 占位 | TTS / 声音克隆(Coming Soon + waitlist 收集) |
| **链布局** | [[avv-token\|AVV]] 在 [[chains/solana\|Solana]];平台支付在 [[chains/base\|Base]] |
| **支付** | USDC(Base 原生),通过 Privy embedded EVM wallet |
| **AVV utility** | USDC 收入周期性 → CCTP 跨链 → Jupiter 买 AVV → SPL burn(详见 [[buyback-burn-program]]) |
| Auth | Privy(EVM + Solana 双 embedded wallet) |
| 主市场 | 海外 EN |
| 团队 | 1-2 人(你 + Claude) |
| 栈 | Next.js 15 + Supabase + Vercel + Privy + Inngest + viem + @solana/web3.js |

V1 **明确不做**:Tip / Boost / Stake / Voice NFT / Governance / 中文 UI / 法币(Stripe)/ 自建链。详见 plan §15。

---

## 60 天里程碑(高层)

起算 2026-04-21,目标 **2026-06-20** 上线 V1 + 提交 KuCoin 申请。

| Week | 主要交付 |
|---|---|
| W1 (4/21–4/27) | repo init、Next + Supabase + Privy hello-world、design tokens、drizzle schema v0、Solana devnet AVV、Base Sepolia USDC.transfer 跑通 |
| W2 (4/28–5/4) | Studio 单图生成跑通、Feed 卡片 + 无限滚动、Base Safe + Solana Squads 多签部署、Sepolia Alchemy webhook |
| W3 (5/5–5/11) | credit_ledger + 新人 100 free + Premium tier;**视频 gate**;AVV mainnet + CertiK 提交;Sepolia 充值入账全流程 |
| W4 (5/12–5/18) | Base mainnet 充值上线;视频接入(若 W3 通过);devnet CCTP + Jupiter swap + SPL burn 全链路 |
| W5 (5/19–5/25) | 内容审核(Moderation + NSFW + 人工 queue);**mainnet 首次 buyback-burn $100 试单** |
| W6 (5/26–6/1) | Remix / follow / save 后端;着陆页;**`/burn` 公开页** |
| W7 (6/2–6/8) | 性能调优;Sentry + PostHog 全埋点;**Dune dashboard 公开** |
| W8 (6/9–6/15) | E2E + 压力测试;内容种子 200 张;TGE + 上 Raydium;**weekly buyback-burn cron 上线** |
| W9 (6/16–6/20) | 软启 + KuCoin 申请提交 |

完整里程碑(含 Gate 检查点 + KuCoin demo 必经路径)见 plan §10。

---

## 链上接口

| 链 | 资产 | 用途 | 地址 / wiki |
|---|---|---|---|
| Solana mainnet | AVV (SPL) | TGE / DEX / 销毁终点 | [[avv-token]],合约地址待 W3 部署后填入 |
| Solana mainnet | Squads multisig | swap + burn 多签 | [[buyback-burn-program]],W2 部署后填 |
| Base mainnet | USDC | 用户支付币种 | `0x833589fCD6eDb6E08f4c7C32D4f71b54bdA02913` |
| Base mainnet | Safe (Gnosis Safe) | 平台收款多签 | [[base-treasury]],W2 部署后填 |
| 跨链 | Wormhole CCTP | Base USDC → Solana USDC | 0 信任,burn-and-mint(Circle 官方) |

---

## 成功标准(60 天后)

提交 KuCoin 时必须达成的数字(完整列表见 plan §12):

- App 上线、`aivive.ai` 解析正常
- 累计注册 ≥ 1000;累计生成 ≥ 5000;累计 publish posts ≥ 1000
- USDC 充值成功 ≥ 50 笔(BaseScan 可查)
- 完成 ≥ 4 次 weekly buyback-burn cycle(Solscan 可查 SPL burn tx)
- Dune dashboard `dune.com/aivive` 公开
- 7 日留存 ≥ 20%
- 0 起提现投诉([[listing-path]] 项目方红线)
- CertiK 审计通过

---

## 关键风险(摘要)

详见 plan §11 完整风险表。最高优先级 4 条:

1. **提现投诉** —— [[listing-path]] 项目方红线;充值失败 / 超额自动退款 + 客服 24h SLA
2. **内容审核失误**(政要 / 儿童 / 真人换脸) —— 双层审核 + prompt 黑名单 + strike 机制
3. **AVV 流动性不足导致 swap 滑点爆炸** —— [[aivive-tokenomics]] Liquidity 18% 必须 W3 全释放到 Raydium pool
4. **CCTP attestation 故障** —— 备用 Allbridge SDK 30 分钟可切换

---

## 与其他 wiki 页面的关系

- **承接**:[[aivive]] 项目 → 本 App 是其交付物清单中的"Dapp Demo (含 AI 社交工具)"
- **依赖**:[[avv-token]] 合约 / [[aivive-tokenomics]] / [[aivive-design]] v0.2(单一事实源,所有 UI 必须读)
- **触发新建**:[[base-treasury]] / [[buyback-burn-program]] / [[chains/base]] / [[chains/solana]](W2 链上线完成后填地址)
- **影响**:[[listing-path]] KuCoin 上所材料、[[aivive-website]] 域名运营、[[aivive-socials]] 营销联动

---

## 开发日志

每个里程碑完成后在 `log.md` 追加一条;关键决策回填本节。

| 日期 | 事件 |
|---|---|
| 2026-04-24 | Plan 完成(初稿 + chain-arch revision);wiki 页创建 |

---

## Open questions / conflicts

- ~~**域名拼写**~~ ✅ 已解决(2026-04-26)— 域名定为 `aivive.ai`,见 [[aivive-website]] §域名拼写决议
- **多签人选**:Base Safe 与 Solana Squads 都需 2/3,具体签名人 TBD,见 [[avv-token]] § Open questions
- **W7 视频功能定档**:default 进 V1,W3 末视基础流稳定性 gate 决定;若砍则 V1.5 补
- **content moderation 中文政要库**:V1 EN 主市场暂用 OpenAI 默认 + 英文政要黑名单;V2 中文上线时补
- **Dune dashboard 谁建**:plan §10 W7 写"公开",但建 Dune SQL 需要专门工时,可能由你或外包 Web3 数据分析师做,W6 末决定

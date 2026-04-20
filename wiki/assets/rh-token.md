---
title: RH Token
type: asset
status: active
tags: [token, solana, spl, redhorse]
sources:
  - raw/RH.csv
updated: 2026-04-18
---

# RH Token

[[red-horse]] 的原生代币,Solana SPL token。

> 来源:raw/RH.csv(rows 2–21, 41)

---

## 基础参数

| Field | Value |
|---|---|
| Token Name | RED HORSE |
| Ticker | **RH** |
| 发行链 | Solana |
| 合约地址 | `A3rk5gtQ2S24Fhz8Ctfhjj2bDgK1SZF7fXvbH1Jty5Bp` |
| 区块浏览器 | https://solscan.io/token/A3rk5gtQ2S24Fhz8Ctfhjj2bDgK1SZF7fXvbH1Jty5Bp |
| Logo | https://image2url.com/r2/default/images/1773640473067-b1d3ec44-73b3-4030-939a-62966c96ddd6.png,详见 [[red-horse-logo]] |
| Total Supply | 10,000,000,000 RH(100 亿) |
| Issuance Time | 2026-01-13,事件页 [[2026-01-13-token-issuance]] |
| Issuance Price | 0.007 USDT |
| Price Decimals | 6(最小价格单位 0.000001) |
| Amount Decimals | 2(最小数量单位 0.01) |
| Opening Price (MEXC) | 0.007 USDT |

---

## 上所流通结构

上线时初始流通分配(来自 RH.csv row 18):

| 来源 | 占比 / 数量 |
|---|---|
| 用户(约 800 人质押) | 5% |
| 流动性池(MEXC) | 1% |

代币在上所前**已在链上流通**(见 RH.csv row 17)。

---

## Tokenomics(代币经济)

代币经济结构详见独立主题页 [[tokenomics]]。摘要:

| Bucket | % |
|---|---|
| Rewards Program | 35% |
| Ecosystem & Partnerships | 20% |
| Liquidity & Market Support | 15% |
| Community Growth & Marketing | 15% |
| Team & Contributors | 10% |
| Treasury / Reserve | 5% |

Vesting schedule:**未公开 / TBD**(RH.csv row 19)。

---

## 已上交易所

- [[mexc]] — 2026-03-20 上线,交易对 RH/USDT

## 目标交易所

- [[kucoin]] — 优先推进
- [[bitget]] — KuCoin 之后

上所路径详见 [[listing-path]]。

---

## 重启后的归档状态(2026-04-18)

- 项目方决定**不做**老 RH 持币用户迁移到新 [[avv-token]](raw/重启/项目方重启信息.md Section 4 明确 `No`)。
- RH 合约 `A3rk5gtQ2S24...` 继续在链上存在,[[mexc]] 交易对保留。
- 孵化方的重启工作主体切换到 **[[avv-token|AVV]]**,RH 不再是上所推进对象。
- 老 [[tokenomics]] 已冻结为历史档案。

## Open questions / conflicts(历史归档)

- ~~RH vesting 是否公开~~ — 不再是优先事项(RH 冻结)
- ~~合约参数(Mintable / Pausable / 多签 / 审计)~~ — 合约已部署且不可改;相关讨论迁移到新 [[avv-token]]
- 如何**公关**老 RH 社区(不迁移、不废弃,需要说法)—— 详见 [[relaunch-plan]]

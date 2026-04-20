---
title: AVV Token
type: asset
status: planned (not yet deployed)
tags: [token, solana, spl, aivive, avv]
sources:
  - raw/重启/项目方重启信息.md
updated: 2026-04-18
---

# AVV Token

[[aivive]] 的原生代币。**尚未部署**,参数为项目方确认版(2026-04-18)。

> 来源:raw/重启/项目方重启信息.md Section 3

---

## 基础参数

| Field | Value |
|---|---|
| Token Name | **AIVIVE** |
| Ticker | **AVV** |
| 发行链 | Solana |
| 合约地址 | 待部署 |

## 合约要求(项目方确认)

| 项 | 值 |
|---|---|
| Mintable | ❌ No |
| Blacklist / Whitelist / Pausable / Upgradeable(Proxy) | ❌ No |
| 交易税 | ❌ No |
| Owner / Treasury 多签 | ✅ Yes |
| 审计 | ✅ **CertiK** |

## 供应 & 价格

| Field | Value |
|---|---|
| Total Supply | 10,000,000,000 AVV(100 亿) |
| Initial Circulating Supply | ~1,000,000,000 AVV(10%) |
| TGE FDV / 目标市值 | **20–30M USDT** |
| Initial Listing Price | **0.002–0.003 USDT** |

---

## Tokenomics

完整分配 & vesting 详见 [[aivive-tokenomics]]。摘要:

| Bucket | % | Cliff | Vesting |
|---|---|---|---|
| Team | 10% | 2 mo | 10 mo |
| Exchange Liquidity(KuCoin / BG) | 18% | — | — |
| Market Maker | 5% | — | — |
| Ecosystem & Community Incentives | 30% | — | — |
| Airdrop / Marketing | 25% | — | — |
| Treasury / DAO Reserve | 10% | 2 mo | 10 mo |
| Advisors | 2% | 4 mo | 8 mo |
| **合计** | **100%** | | |

- **无** Private / Seed bucket
- **无** Public Sale / IDO bucket

---

## 与 [[rh-token]] 的关系

- 老 [[rh-token]] 持币用户 **不做快照迁移**(项目方 Section 4 明确 `No`)。
- AVV 是**全新合约**,与 RH 合约无任何链上关系。

---

## Open questions / conflicts

- Ecosystem / Airdrop / Market Maker / Liquidity 四个 bucket 的 **cliff & vesting 未填**,raw 中对应格为 `-`。上所前需要补全。
- 合约部署时间节点未定,但整体要求 ASAP(见 [[aivive]])。
- 多签钱包的**签名人 & 阈值**未定。
- CertiK 审计的预算 / 档期 / 合同方待确认。

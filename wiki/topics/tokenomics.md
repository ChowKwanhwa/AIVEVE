---
title: RH Tokenomics (legacy)
type: topic
status: legacy (superseded by [[aivive-tokenomics]])
tags: [tokenomics, economics, redhorse, legacy]
sources:
  - raw/RH.csv
  - raw/项目方确认清单.md
  - raw/project-confirmation-checklist.md
updated: 2026-04-18
---

# Tokenomics — [[rh-token]] 代币经济(历史)

> ⚠️ **历史档案**。2026-04-18 项目方决定重启走新代币 **AVV**,RH tokenomics 冻结。新项目经济结构见 **[[aivive-tokenomics]]**。

> 来源:raw/RH.csv rows 11–21; raw/项目方确认清单.md 第三节

---

## 发行参数

| Field | Value |
|---|---|
| Total Supply | 10,000,000,000 RH |
| Issuance Time | 2026-01-13([[2026-01-13-token-issuance]]) |
| Issuance / Opening Price | 0.007 USDT |
| TGE FDV | 未明确给出(10B × 0.007 = 70M USDT 名义) |
| 初始流通 | 用户 5% + MEXC 流动性 1%(RH.csv row 18) |
| IDO | — 无 |
| Private / Seed | — 无 |

---

## 分配方案(已提交版)

来自 raw/RH.csv row 19:

| Bucket | % |
|---|---|
| Rewards Program | **35%** |
| Ecosystem & Partnerships | **20%** |
| Liquidity & Market Support | **15%** |
| Community Growth & Marketing | **15%** |
| Team & Contributors | **10%** |
| Treasury / Reserve | **5%** |
| **合计** | **100%** |

Vesting schedule:**Not announced / TBD**(RH.csv row 19)。

---

## 分配方案(确认清单模板)

[[project-confirmation-checklist]] 第三节给出的标准模板与 CSV 中分类不同:

| Bucket(模板) | 是否在已提交版中有对应 |
|---|---|
| 团队(Team) | ✅ 10%(Team & Contributors) |
| 投资人(Private / Seed) | ❌ CSV 中为 "-" |
| 公募 / IDO | ❌ CSV 中为 "-" |
| 交易所流动性(KuCoin / BG) | ⚠️ 部分(Liquidity & Market Support 15% 含 MEXC,是否涵盖 KuCoin/BG 待确认) |
| 做市商 | ⚠️ 模板项,CSV 未拆分 |
| 生态 & 社区激励 | ✅ Ecosystem 20% + Community 15% |
| 空投 / 市场活动 | ⚠️ 归到 Community 15% 内? |
| 金库 / DAO 储备 | ✅ 5% |
| 顾问 | ❌ CSV 未列 |

---

## Open questions / conflicts

1. **Vesting schedule 未公开**,无法交付白皮书 V1 与上所 KYC。需项目方补齐 cliff & linear vesting 每 bucket 参数。
2. **CSV 分类 vs. 清单模板分类不一致**。需在重启 [[relaunch-plan]] 中重新整理,或明确 CSV 已是最终版。
3. **交易所流动性拆分**:KuCoin / BG 的流动性预算是否已从 15% Liquidity bucket 中预留,还是需要另行规划。
4. **合约设定**(Mintable / Pausable / Owner 多签 / 审计)未定,详见 [[rh-token]] 与 [[project-confirmation-checklist]] 第 3.1 节。

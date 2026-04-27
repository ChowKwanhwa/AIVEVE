---
title: Aivive Whitepaper
type: asset
status: v0.1 split + 商业升级 完成 (2026-04-27)
tags: [whitepaper, aivive, gitbook-ready]
sources:
  - raw/重启/项目方重启信息.md
  - outputs/whitepaper/  (multi-page GitBook structure)
updated: 2026-04-27
---

# Aivive Whitepaper

[[aivive]] 的白皮书,由孵化方承接编写。已重构为 **GitBook 标准 multi-page 结构**(README + SUMMARY + 13 sections),Git Sync 推到 GitBook 直接渲染成 docs site。

> 来源:raw/重启/项目方重启信息.md;v0.1 multi-page split + 商业升级版起草于 2026-04-27

---

## 状态

- ✅ **v0.1 multi-page split + 商业升级 完成** — `outputs/whitepaper/`(15 文件 / GitBook-ready)
- 老的单文件 v0.1-draft.md 已删除(被 multi-page 替代)
- 待:网络修好 → API/Git Sync 上 GitBook → 项目方 review → 视觉版面(plan §10 W7 排) → 中文版翻译 → 审计完成后填合约地址 → v1.0 发布
- 不复用 [[red-horse-whitepaper]](老 GitBook 属于历史项目)

## 文件结构(`outputs/whitepaper/`,GitBook-ready)

```
outputs/whitepaper/  (14 文件)
├── README.md           Cover + Abstract (含 hero quote + market hook)
├── SUMMARY.md          GitBook TOC (4 大 Part 分组)
├── 01-introduction.md  §1 + §1.0 市场机会(2027 $50B+ 数据表)
├── 02-vision.md        §2 三大原则 + 拒绝清单
├── 03-network.md       §3 跨链架构 + buyback-burn cycle
├── 04-product.md       §4 5 surface + 双循环 + 三 tier (Ultra = gpt-image-2)
├── 05-architecture.md  §5 + Drizzle ledger schema 代码 + Alchemy webhook 代码
├── 06-tokenomics.md    §6 + §6.5 估值公式 + §6.6 Vesting 可视化
├── 07-token-utility.md §7 + §7.5 通缩方程 + 场景表 + burn cron 伪代码
├── 08-roadmap.md       §8 V1 → V1.5 → V2 → V2+
├── 09-team.md          §9 yu-network-srl + taehun-kim + Claude harness
├── 10-audits.md        §10 CertiK + 多签 + 提现完整性
├── 11-risks.md         §11 7 类风险
└── 12-resources.md     §12 链接 + 术语表
```

> 2026-04-27 用户反馈调整:
> - Disclaimer 节已删除(用户:"不需要 disclaimer,公开 GitBook 版"),不再补回
> - OpenAI Ultra tier 模型从 `gpt-image-1` → **`gpt-image-2`**(同步更新到 plan + aivive-app wiki)
> - 加 4 个 Mermaid 图表(GitBook 原生渲染,markdown 源码可控):
>   - §1.0 — `xychart-beta` bar chart:AI image-gen 市场 5 年增长曲线
>   - §3.3 — `flowchart`:USDC → CCTP → Jupiter → SPL Burn 全流程图
>   - §6.2 — `pie chart`:7 类 tokenomics 分配饼图(★ 用户点名要)
>   - §7.2 — `sequenceDiagram`:三段式资金流时序图(User / Treasury / CCTP / Jupiter / AVV)

## v0.1 商业升级版关键新增

| 节 | 新增内容 |
|---|---|
| Abstract | 市场机会 hook($50B+ 2027 投影)+ "AI made content infinite. We made one thing scarce." 锚句 |
| §1.0 | 新增 "Market Opportunity" 数据表(2023-2027 行业 trend) |
| §5.5 | Drizzle ORM 真实代码 schema + Alchemy webhook handler 完整 TypeScript |
| §6.5 | FDV / Initial Market Cap / Circulating Ratio 三个公式推导 |
| §6.6 | Vesting 可视化 ASCII 时间轴 |
| §7.5 | 通缩方程 `S(t) = S₀ - ∫₀ᵗ Burn(τ) dτ` + 场景表(4 档 weekly revenue → annualized burn rate)+ swap-and-burn cron 完整 Inngest 伪代码 |

## 锁定的关键决策

- **叙事主线**:AI Consumer Economy(用户 2026-04-27 选定)
- **Hero claim**:"What if the way you fund an AI product was the same as the way you make its asset rarer?"
- **品牌词**:大写 Aivive / Give / Vive(关键位置斜体)
- **结构对标**:ILITY Network 风格(类目宣称 + 机制 + 大结局)

---

## Open questions / conflicts

- ~~项目方未明确赛道红线~~ ✅ 已解决(2026-04-27 用户拍板"AI Consumer Economy"叙事)
- **多签人选 TBD** — Squads (Solana) + Safe (Base) 都需 2-of-3 签名人具体名单。等 [[avv-token]] 多签结构敲定一起更新到 §10
- **Advisor 名单 TBD** — 2% allocation 已留位,人选未定。TGE 前披露
- **CertiK 审计报告链接** — 待审计完成后填入 `aivive.ai/docs/audits`
- **中文版翻译** — V1 launch 日 / 中文 KOL 投放需要,目前无中文版本
- **官方 docs 站** — `aivive.ai/docs/whitepaper` 未上线;v0.1 评审完成后随 [[aivive-website]] V1 一起部署

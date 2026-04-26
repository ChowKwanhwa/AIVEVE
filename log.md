# Log — 追加式活动日志

> 每一次 ingest(摄取新资料)、query(查询综合)、lint(健康检查)都在此追加一条记录。
> 只追加,不删除,不修改历史条目。新条目写在文件末尾。

---

## 2026-04-18 — Wiki 初始化(Bootstrap)

**类型**: ingest (bulk)
**操作者**: Claude (Opus 4.7)
**触发**: 用户指令 "根据 karpathy 的 gist,把现在这个 codebase 转成我的个人 wiki"

**处理的 raw 源文件**:
- `raw/RH.csv` — 项目基础信息 & tokenomics 提交表(Project Details)
- `raw/RedHorse项目重启.md` — 项目方重启沟通纪要(2026-04-16)
- `raw/links.md` — 项目现有资料链接汇总
- `raw/project-confirmation-checklist.md` — 英文版确认清单
- `raw/项目方确认清单.md` — 中文版确认清单
- `raw/报价要求.md` — 报价/范围说明
- `raw/参考项目/quantra.md` — 参考项目 Quantra 渠道汇总
- `raw/logo/logo.png` — 品牌 Logo 原图
- `raw/备份/RH.xlsx` — RH 数据 Excel 备份

**生成的 wiki 页面**:
- projects: [[red-horse]], [[quantra]]
- assets: [[rh-token]], [[red-horse-website]], [[red-horse-whitepaper]], [[red-horse-twitter]], [[red-horse-telegram]], [[red-horse-logo]]
- exchanges: [[mexc]], [[kucoin]], [[bitget]]
- entities: [[yu-network-srl]]
- people: [[taehun-kim]]
- topics: [[tokenomics]], [[relaunch-plan]], [[ai-social-positioning]], [[listing-path]], [[brand-direction]]
- events: [[2026-01-13-token-issuance]], [[2026-03-20-mexc-listing]], [[2026-04-16-relaunch-agreement]], [[2026-04-18-incubation-kickoff]]
- checklists: [[project-confirmation-checklist]]

**产物**:
- `CLAUDE.md` — schema 与流程
- `index.md` — 内容目录
- `log.md` — 本文件

**备注 / 发现的 Open Questions**(已在对应页面 `## Open questions` 节登记):
- Tokenomics 分配方案:`raw/RH.csv` 与 `raw/项目方确认清单.md` 结构不同,前者已给出 35/20/15/15/10/5% 分配;后者模板仍为空待填。需要项目方确认是否以 CSV 中数据为准,或按重启后重新设计。
- Vesting schedule 在 RH.csv 中标为 "Not announced / TBD",需项目方补充。
- 重启方案中 "衍生 DAO 生态"的具体含义未定义 — 详见 [[relaunch-plan]]。
- 现有 2800 Twitter 粉丝基础上,是否需要买 5w+ 号,执行路径未定 — 详见 [[red-horse-twitter]]。
- 韩国人站台 vs. 需要外籍 CTO/CEO 站台,暂未最终选择 — 详见 [[relaunch-plan]]。

---

## 2026-04-18 — Ingest: 项目方回填确认清单(品牌反转)

**类型**: ingest
**操作者**: Claude (Opus 4.7)
**触发**: `raw/重启/项目方重启信息.md` 出现(项目方 2026-04-18 回填的英文版确认清单)

**新增原始源**:
- `raw/重启/项目方重启信息.md`(新子目录 `raw/重启/`)

**关键转向**:项目方**不沿用** Red Horse 品牌,**重启后改名为 Aivive (Ticker: AVV)**。具体决策:

- 品牌:重命名 + 新 Logo(由孵化方设计),风格授权孵化方主导
- 域名:`aiavive.ai`,项目方自行注册,无需孵化方代注
- 代币:Solana 上的 **AVV**,10B 总量,1B 初始流通,FDV 20–30M,上所价 0.002–0.003 USDT
- 合约:Not Mintable / Not Pausable / 无税 / 多签 / **CertiK 审计**
- 分配:Team 10% / Liquidity 18% / MM 5% / Ecosystem 30% / Airdrop 25% / Treasury 10% / Advisors 2%;4 个 bucket vesting 未填
- 老 RH 持币用户:**不做**快照迁移
- 社媒:**全新**渠道,不复用老 Red Horse 账号
- 交付:**ASAP**
- 白皮书赛道红线:留空,待孵化方提案

**新建的 wiki 页面**:
- projects: [[aivive]]
- assets: [[avv-token]], [[aivive-website]], [[aivive-whitepaper]], [[aivive-socials]]
- topics: [[aivive-tokenomics]]
- events: [[2026-04-18-project-confirmation-reply]]

**更新的 wiki 页面**(反映品牌反转):
- [[red-horse]] — 标记为 legacy,指向 [[aivive]] 作为继任项目
- [[brand-direction]] — 反转为"重命名 + 新 Logo"
- [[relaunch-plan]] — 重写决策清单、交付物、open questions、下一步
- [[project-confirmation-checklist]] — 把 pending 改为已答复,补入回答值
- [[tokenomics]] — 标记为 RH 历史档案
- [[rh-token]] — 补"不做迁移"说明与归档状态
- [[red-horse-twitter]] / [[red-horse-telegram]] — 标记 legacy + "不复用"
- [[listing-path]] — 主体从 RH 切换到 AVV
- [[ai-social-positioning]] — 与 Aivive 新品牌对齐
- [[2026-04-18-incubation-kickoff]] — 补入当日品牌反转事件
- `CLAUDE.md` — 补 `raw/重启/` 子目录、项目简介更新为"Aivive 当前 + Red Horse 历史"
- `index.md` — 按"当前项目 / 历史归档"重排

**新增的 Open Questions**:
- Aivive 中文名未定
- 品牌名 `Aivive` vs. 域名 `aiavive.ai` 拼写不一致 — 需跟项目方确认是否手误
- [[avv-token]] 四个 bucket(Ecosystem / Airdrop / MM / Liquidity)的 cliff + vesting 未填
- 多签签名人 & 阈值未定
- 白皮书赛道红线:项目方留空,孵化方需提 2–3 套叙事
- 老 Red Horse 社区的公关善后方案

---

## 2026-04-19 — Ingest: 品牌设计系统(DESIGN.md)

**类型**: ingest + 新子体系
**操作者**: Claude (Opus 4.7)
**触发**: 用户引入 VoltAgent/awesome-design-md(Google Stitch DESIGN.md 概念)作为品牌视觉交付方式

**引入的外部知识**:
- VoltAgent/awesome-design-md 仓库结构(68 家品牌,markdown 驱动,面向 AI agent 可读)
- Google Stitch DESIGN.md 概念
- 完整内容已迁至 `getdesign.md`(需 `npx getdesign@latest add <brand>` 拉取)

**新增 wiki 子目录**:
- `wiki/design/` — 设计系统专区
- `wiki/design/references/` — 外部参考指针

**新增 wiki 页面**:
- [[aivive-design]] — **Aivive DESIGN.md v0.1**(完整设计系统:13 节,覆盖色/字/间距/圆角/阴影/motion/图标/插图/tone/组件/模式/消费指引)
- [[framer-DESIGN]] / [[linear-DESIGN]] / [[cal-DESIGN]] — 外部参考指针,指向 getdesign.md

**设计决策(已锁定,在 [[aivive-design]] 里定值)**:
- 调性三词:**Alive / Warm / Sharp**
- 主色:紫 `#5B3BEE` + 暖粉 `#FF8A5C` + 电光青 `#4FFFD8`(对应 AI / Give / Vive 三层语义)
- **完全禁用**红色系(与 [[red-horse]] 视觉血缘切断)
- 字体:Geist + IBM Plex Serif(关键词"Give / Vive"用衬线)
- Signature motion:2.8s Breathe 呼吸循环,承载"AI is alive"叙事
- 模式:Dapp / 官网深色默认,白皮书 / Docs 浅色
- 图标:Lucide 1.5px stroke
- 插图**禁**:扁平矢量、线条插画、机器人/电路板套路、马的意象

**品牌叙事决策**:
- 采纳**双释义**策略:主读 **AI + Give**(项目方原义),副读 **AI + Vive**(英语语感自然联想)—— 解决英语母语者语感和项目方定义之间的张力

**更新的 wiki 页面**:
- [[brand-direction]] — 工作项改成 DESIGN.md 已完成 + 给项目方"1 主 2 变"呈送方案;新增双释义风险 Open question
- `CLAUDE.md` — 新增 §4 "设计系统(单一事实源)",规定所有 UI/前端任务必须先读 [[aivive-design]]
- `index.md` — 新增 "Design(设计系统)" 分类

**新增的 Open Questions**(已登记到 [[aivive-design]] §12):
- Logo mark 矢量未产出
- 中文文案在中文名敲定前以 "Aivive" 原词出现,不音译
- Breathe 动画 2.8s 节奏待可用性测试微调
- 站台人/Advisor 是否需要专属视觉模版

---

## 2026-04-19 — Ops: Brand Designer 招聘需求

**类型**: 新产出(ops 类)
**操作者**: Claude (Opus 4.7)
**触发**: 用户要招一位设计师做 Logo / 海报 / 一图读懂 / 社媒 / 白皮书视觉

**新增 wiki 子目录**:
- `wiki/ops/` — 运营 / 招聘 / 协议 / 流程类文档

**新增 wiki 页面**:
- [[designer-hiring]] — 9 节 JD:项目背景 / 交付物(7 项必 + 3 项加分)/ 核心能力 / 加分项 / 调性自筛 / 交付节奏(4 周)/ 合作方式 / 申请流程 / 硬刷条件

**关键 tailoring 点**:
- JD 明确"按 [[aivive-design]] 落地,不做品牌提案"—— 避免候选人反复要求自由度
- 禁区清单直接抽自 DESIGN.md:红色 / 扁平矢量 / 线条插画 / 马的意象 / 机器人套路 / meme 贴纸 / 企业蓝
- 4 周里程碑对齐 [[listing-path|KuCoin ASAP]] 节奏
- 设 "秒刷硬条件" 过滤:无 Web3/AI/发光作品 / 只有 Logo 单品 / 不能本周开工

**留给用户填的占位**:
- 微信 / 邮箱 / Telegram 联系方式
- 预算区间
- 版权归属 & NDA 细节

**更新的 wiki 页面**:
- `CLAUDE.md` — 目录结构新增 `wiki/ops/`
- `index.md` — 新增 "Ops" 分类

---

## 2026-04-20 — Aivive 品牌 v0.2 迁移(紫色退役 → Aqua 主色)

**类型**: ingest (design-system migration)
**操作者**: Claude (Opus 4.7)
**触发**: 用户指令 "不要用紫色,紫色太像AI了" → "用Aqua当主色"

**动机**:
- 紫色/violet 渐变在 AI 产品中已成视觉陈词(OpenAI / Anthropic / Midjourney / Copilot 同质化)
- Aivive 需与"AI 彩虹渐变"拉开距离,主色切换为 aqua,品牌色双主 aqua + coral(暖)

**SSOT 更新**:
- `wiki/design/aivive-design.md` v0.1 → v0.2 重写:
  - §2.1 Aqua 新主色(Tailwind anchor aqua/500 = `#4FFFD8`)
  - §2.3 Ink 去紫化(hue 260° → 160°),9 档 teal-black
  - §2.5 渐变简化为 2-stop `aqua → coral`(退役 3-stop violet→coral→aqua)
  - §2.6 "Do Not" 新增 "不用紫色"
  - §9 按钮 primary 在 dark 模式文字反转为 ink/950(因 aqua 太亮)
  - §13 记录完整迁移说明

**Figma 文件 1 — Brand Brief(`zUkPA30Kxd2pI2Tq143yAo`)**:
- Primitives 新增 aqua/200 #A8FFEB / aqua/700 #0E9E80 / aqua/800 #0B7A63 / aqua/900 #08584A
- Ink 9 档全部更新为 v0.2 teal-black 值
- 语义 token 重绑(Dark↔Light):`color/brand/primary`、`color/text/brand`、`color/text/on-brand`、`color/brand/vive`
- 重建 5 页:Cover / ④ Color Palette / ⑥ Gradient Library / ⑨ Do's & Don'ts / ⑩ Moodboard
- 硬编码 violet 补丁 12 处:Logo Brief 文案、Poster Specs 5 个画幅渐变、Poster Specs glow 椭圆、Social Kit Specs OG/avatar/story/banner 5 个渐变

**Figma 文件 2 — Visual Guide(`buOQAK3El7SLaeSOEoOFjj`)**:
- 相同 primitive + ink + 语义 token 迁移(brand/primary, primary-hover, primary-pressed, vive, text/brand, text/on-brand)
- `color/status/info` 重绑 violet/500 → aqua/400(v0.2 无专用 info 色,复用 aqua 家族)
- Effect styles 修复:shadow/1..3 紫黑色 → ink/950;glow/violet 保留位但颜色改为 aqua + 描述标记 DEPRECATED
- 组件修复:Hero 两层渐变(linear + radial vignette)、Button primary hover 发光、Input focus ring — 全部去紫
- 5 个组件页的 page background 从 `#0B0720` → `#08100E`(ink/950)
- Cover & Foundations 版本号文案 v0.1 → v0.2
- Input 描述文案 "violet glow" → "aqua glow"
- Foundations 标题 "glow violet" → "glow aqua"
- 保留 5 个 violet/* primitives(violet/300..700)但标记 DEPRECATED 描述(非破坏性迁移,防未知外部引用)

**影响的 wiki 页面**:
- `wiki/design/aivive-design.md` — 核心重写

**为什么紫色原语不删除**:
- Figma Variables 在模式/文件/库间的交叉引用无法可靠静态追踪,删除可能破坏订阅本库的其他文件
- 在 description 里声明 DEPRECATED 是惯例做法,未来清理周期统一删

---

## 2026-04-24 — Aivive App V1 规划完成 + chain-arch 双链 hybrid

**类型**: planning + ingest (新 wiki 页 + plan)
**操作者**: Claude (Opus 4.7)
**触发**: 用户指令 "为AIVIVE规划一个App;集合 TTS / 声音克隆 / 文生图 / 文生视频, 2 个月内上 KuCoin", 用 superpowers brainstorming + plan mode 全流程

**产物**:
- `/Users/ericc/.claude/plans/aivive-app-ai-saas-tts-aivive-crypto-2-silly-lovelace.md` — 完整 plan(16 节, 含 chain-arch 修订记录 §16)
- `wiki/projects/aivive-app.md` — 新 wiki 页(对外可见状态 + 决策摘要 + 上线 metric)
- `index.md` — Assets 节加 [[aivive-app]] 链接

**MVP 形态决策**:
- 经 brainstorm 由用户从 3 个切法(全能 Studio / 单点 Hero / AI Social Feed)中选 **C. AI Social Feed**(类 Civitai/Pixiv)
- Hero 模型 = **文生图**(用户指出"视觉化, 适合交易所演示")
- 视频 V1 待 W3 末 gate;TTS / 声音克隆 V1 占位
- 主市场海外 EN, 团队 1-2 人(你 + Claude), 栈 = Next 15 + Supabase + Vercel + Privy + Inngest + viem

**Chain-arch 关键决策(2026-04-24 修订)**:
- 用户原议"自建 EVM 测试链给 listing team 看", 经评估后否决:2 周成本不换 KuCoin 信任, normie 流失
- 用户改为"TGE 走 Solana, 平台支付走 EVM, 比较方便", 进一步确认 = **Base mainnet** 不自建链(用 anvil + Base Sepolia 做 dev)
- 支付币种 = **USDC**(Base 原生);AVV 不直接被用户使用
- AVV utility 实现 = **平台 USDC 收入周期性 → CCTP 跨链 → Jupiter 买 AVV → SPL burn**(deflationary anchor, 类 BNB/GMX/SNX 模式)
- 三段资金流见 plan §7;数据模型新增 `cross_chain_transfers` `burn_runs` 表

**60 天里程碑**:
- 起算 2026-04-21, 目标交付 **2026-06-20** 上线 V1 + 提交 KuCoin 申请
- W1 现起 = repo init + Next/Supabase/Privy hello-world + design tokens + drizzle schema v0
- 4 个 Gate 检查点(W3 视频 / W4 充值 / W5 审核 / W7 DAU)

**待新建 wiki 页(W2-W3 链上线后填地址)**:
- [[base-treasury]] — Base Safe 多签
- [[buyback-burn-program]] — Wormhole CCTP + Jupiter swap + SPL burn cron 配置
- [[chains/base]] / [[chains/solana]] — 双链地址 / 合约 / 依赖

**Open questions(已写入 [[aivive-app]] 页)**:
- 域名 `aivive.ai` vs `aiavive.ai` 拼写
- 多签人选 TBD
- 视频 V1 进 / 砍 W3 末决定
- Dune dashboard 谁建 W6 末决定
- 中文政要库 V2 中文上线时补

**未变更**:wiki schema / [[aivive-design]] v0.2 / [[avv-token]] / [[aivive-tokenomics]] 不动;App 是新 asset 不影响已有决策

---

## 2026-04-24 — Ops: Social Content Bank V1 (Mystery Phase)

**类型**: 新产出 (ops 类)
**操作者**: Claude (Opus 4.7)
**触发**: 用户优先级转向 — App 仍在 W1 scaffold 阶段, 但运营 Twitter / 出海报文案是更紧急的当务之急

**关键策略决定**(2 轮迭代收敛):
- 第 1 版: 含 $AVV ticker + burn 机制 + 上 KuCoin 故事
- 用户反馈: "项目还非常前期, 不要提到 $AVV, 弄点神秘感, 多聊 AI / AI Agent / Harness 等深度内容"
- **最终 V1 = 完全不卖币、不卖产品**, 建立"懂 AI 的 thinker"账号人设, 先吸 AI 圈再降到 Web3 人群

**新建 wiki 页**:
- [[social-content-bank-v1-mystery-phase]] — 11 节, 含:
  - §0 品牌硬约束 (引 [[aivive-design]] §8 + plan §11/15/6 红线)
  - §1 Bio / Handle / Pinned 终选
  - §2 推文 28 条 6 类 (A 深度 8 / B 神秘 5 / C 美学 4 / D 互动 5 / E build-in-public 3 / F 身份 3)
  - §3 海报 5 张 (M1 Hero / M2 Loop / M3 Three Words / M4 Harness / M5 Day Counter)
  - §4 首周 7 天发布日历 (Day-Time-推文-配图-目的)
  - §5 KOL 互动框架 + Tier 0/1 短名单
  - §6 Reply Hook 库 (5 类 + 红线)
  - §7 Thread 模板 3 条 (T1 harness / T2 generation vs taste / T3 60 天 5 件事)
  - §8 Telegram 启动包 (channel / chat / 群规 / 5 条首条消息)
  - §9 Phase 2 揭面纱推文 (W2-W3 触发条件 + P2A-F 共 8 条)
  - §10 ops 提醒
  - §11 versioning (V1 → V2 → V3 切版本规则)

**关键品牌约束 (V1 全篇红线)**:
- ❌ $AVV ticker / 上所名称 / 价格 / TGE 日期 / "to the moon"
- ❌ 主动提 [[red-horse]] 老社区
- ❌ 海报视觉里政要 / 真人 / 儿童
- ❌ 紫色 / 红色 (沿用 [[aivive-design]] v0.2)
- ✅ 只用 aqua + coral + ink (teal-black hue 160°)
- ✅ 大写品牌词 Aivive / Give / Vive (关键位置可衬线)

**更新的 wiki 页**:
- `index.md` — Ops 节加 [[social-content-bank-v1-mystery-phase]] 链接

**Open questions** (已写入 wiki 页 §Open questions):
- Twitter handle (@aivive_ / @aivive_ai / @aivive_io) 4 个候选都未确认可用
- TG 命名一致性 (`_chat` 子目录是孵化方惯例还是项目方偏好)
- 谁来发推 (孵化方代发 vs. 项目方账号), 见 [[aivive-socials]] 早期 open question
- 5w+ 粉老号买号方案 (raw/报价要求.md) 在新品牌下是否仍执行

**未变更**:[[aivive-design]] / [[brand-direction]] / [[aivive-app]] / [[avv-token]] 不动

---

## 2026-04-26 — Ingest: 社媒 handle 确认 + 域名拼写决议 + bio/blurb 落档

**类型**: ingest (项目方提供的运营信息) + ops 类新产出
**操作者**: Claude (Opus 4.7)
**触发**: 用户提供 7 个 social URL + 1 个 email + website,确认所有 channel 已创建

**输入**:
```
Twitter:    https://x.com/AIVIVEHQ
Telegram:   https://t.me/AIVIVEHQ
YouTube:    https://www.youtube.com/@AIVIVEHQ
Medium:     https://medium.com/@aivive
Link3:      https://link3.to/aivive
Email:      contact@aivive.ai
Website:    https://aivive.ai
```

**关键决议(2 个 open question 一并解决)**:

1. **域名拼写**:`aiavive.ai`(项目方原 raw 笔误)→ 实际为 **`aivive.ai`**
2. **Handle**:Twitter / TG / YouTube 统一 `@AIVIVEHQ`(HQ 后缀防仿冒);Medium / Link3 用 `aivive`(无后缀)

**批量操作**:
- `sed` 全仓替换 `aiavive.ai` → `aivive.ai`(影响 13 个文件)
- `sed` 全仓替换 `@aivive_` → `@AIVIVEHQ`,`@aivive_chat` → `@AIVIVEHQ_chat`
- 修复 sed 误伤的历史注释(`wiki/assets/aivive-website.md` §域名拼写决议保留 `aiavive.ai` 原始拼写以记录笔误)
- 8 个文件的"拼写未确认"/"待澄清"open question 标记为 ✅ 已解决

**新建 wiki 页内容**:
- [[aivive-socials]] 重写:从"未创建"→列出全部 7 个已创建 channel + handle 命名约定 + 还未开 channel + 仍未解的 open question
- [[aivive-website]] 重写:加 §域名拼写决议节,标明 `aivive.ai` 为最终值

**新建 outputs**:
- `outputs/copy/bio-and-blurb.md`(2026-04-26):
  - Part 1 Bio 包(7 个平台:Twitter/TG/Discord/Medium/Link3/Email signature 等)
  - Part 2 Blurb 包(VC / 项目方 / AI builder 三种受众 × 三种长度 + 4 个 ask 模板 + 1 个完全神秘版)
  - Part 3 使用建议 + 公开 vs 私下双红线 checklist

**更新的 wiki 页**:
- [[aivive]] — 域名行 ✅,社群交付物 ✅
- [[aivive-app]] — 域名 open question 划掉
- [[aivive-design]] — §12 open question #2 划掉
- [[brand-direction]] — open question 域名行划掉
- [[relaunch-plan]] — 2 处域名相关划掉
- [[project-confirmation-checklist]] — 域名行 ⚠️ → ✅
- [[2026-04-18-incubation-kickoff]] — 域名核实 todo 打勾
- [[social-content-bank-v1-mystery-phase]] — §1 Bio/Handle 节重写为"实际使用 handles",§Telegram 节标注 channel 已建 chat 待建
- `outputs/copy/bio-and-blurb.md` — Linktree → Link3,加 handle 速查头部

**仍未解的 open question(已记录在 [[aivive-socials]])**:
- 5w+ 粉老号买号方案是否在新品牌下执行
- 社媒账号所有权(孵化方代持 vs 项目方持有)
- TG chat group 是否要建 + handle 是否用 `@AIVIVEHQ_chat`
- Twitter handle 大小写显示统一(全大写 vs mixed case)

**未变更**:plan / [[aivive-design]] 颜色系统 / [[avv-token]] 合约信息 / [[aivive-tokenomics]] 不动

---

# Personal Wiki — Schema & Workflows

> 本仓库是一个遵循 [Karpathy LLM-Wiki 模式](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f) 的个人 wiki。
> 三层架构:`raw/`(不可变原始资料) → `wiki/`(LLM 生成并持续维护的结构化页面) → 本文件(schema 与流程)。

---

## 一、目录结构

```
/
├── CLAUDE.md           # 本文件 — schema、约定、流程
├── index.md            # 内容目录 — 按主题/实体分类列出所有 wiki 页面
├── log.md              # 追加式日志 — 每次 ingest / query / lint 都记录
├── raw/                # 原始资料(不可变,只追加)
│   ├── *.md            # 原始文档
│   ├── *.csv / *.xlsx  # 结构化数据
│   ├── logo/           # 图片/素材
│   ├── 参考项目/       # 外部项目参考资料
│   ├── 备份/           # 历史备份
│   └── 重启/           # 重启阶段文档(项目方回填清单等)
└── wiki/               # LLM 维护的 wiki 页面
    ├── projects/       # 项目主页(本项目 + 参考项目)
    ├── assets/         # 项目资产(代币、域名、社媒账号、白皮书等)
    ├── exchanges/      # 交易所相关页面
    ├── entities/       # 法律实体、合作方
    ├── people/         # 人物
    ├── topics/         # 跨实体主题(Tokenomics、定位、叙事等)
    ├── events/         # 时间线事件(上所、融资、里程碑等)
    ├── design/         # 设计系统(DESIGN.md 单一事实源 + 外部参考指针)
    └── ops/            # 运营 / 招聘 / 协议 / 流程
```

---

## 二、Wiki 页面规范

### 文件头 frontmatter

每个 wiki 页面都以 YAML frontmatter 开头:

```yaml
---
title: 页面标题
type: project | asset | exchange | entity | person | topic | event
status: active | archived | pending
tags: [redhorse, token, solana]
sources:
  - raw/RH.csv
  - raw/RedHorse项目重启.md
updated: 2026-04-18
---
```

### 正文约定

1. **Obsidian 风格内链**:跨页引用一律使用 `[[页面名]]` 或 `[[页面名|显示文本]]`。
2. **引用原始资料**:在正文里用 `> 来源:raw/xxx.md` 标注每个关键事实的出处。
3. **日期一律绝对化**:`"周四"` 必须写成 `2026-04-18`。
4. **按主题聚合,不是按来源聚合**:同一个实体的信息,即使散落在多个 raw 文件里,也应当在对应 wiki 页面里合并。
5. **保留冲突**:若 raw 资料之间存在矛盾,**不要**自行决断,在页面底部用 `## Open questions / conflicts` 显式列出。
6. **小文件优先**:单页 150–400 行为宜,超长时拆分。

---

## 三、核心工作流

### 1. Ingest(摄取新资料)

当用户新增 `raw/` 下的文件时:

1. 阅读新文件,提取实体、事实、关系。
2. 判断每条信息应归入哪个已有 wiki 页面,或需要新建哪个页面。
3. 更新相关 wiki 页面(可能涉及 5–15 个),添加/修改事实,补上 `[[内链]]`。
4. 更新 `index.md`:新页面加入目录。
5. 在 `log.md` 末尾追加一条 ingest 记录(日期、来源文件、影响页面清单、摘要)。
6. 不删除 raw 资料。原始文件永远保留。

### 2. Query(查询)

当用户提问时:

1. 先查 `index.md` 与 `wiki/` 中的相关页面(Obsidian-style 搜索)。
2. 综合多页信息作答,**每条事实附上 wiki 页面来源**(如 `[[rh-token]]`)。
3. 若查询过程中产生了新洞察、总结或对比,**主动沉淀为新 wiki 页面或补充已有页面**。
4. 在 `log.md` 追加一条 query 记录(日期、问题摘要、引用页面、是否产生新页面)。

### 3. Lint(定期健康检查)

按需(或按用户指令)执行:

1. **孤儿页面**:没有被任何其他页面 `[[链接]]` 到的 wiki 页面,提示是否归档或在 `index.md` 中补链。
2. **矛盾检测**:同一事实在不同页面有不同值(例如 TGE 价格、总量),列出待用户裁决。
3. **过时信息**:与当前 raw 中最新文件冲突的旧事实,提示更新。
4. **空缺区域**:checklist 类页面中长期未填的条目,提示追问项目方。
5. **日期漂移**:含 `TBD` / `待定` 的条目统计,生成 follow-up 清单。
6. lint 结果写入 `log.md`。

---

## 四、设计系统(单一事实源)

所有 [[aivive]] 相关的 **UI / 前端代码 / 营销物料 / 品牌视觉** 任务,**必须先读** `wiki/design/aivive-design.md`,按其中定义的 color / typography / spacing / motion / component token 产出。

- 不写 hex 字面量,引用 token(例:用 `--violet-500` 而不是 `#5B3BEE`)
- 不做 token 外的自创色 / 字号,除非先在 [[aivive-design]] 里加条目
- 本文件 v0.1 已合成 Framer / Linear / Cal.com 三份参考,外部参考只作对标,不作权威

新建 UI 相关 agent prompt 或 Tailwind config 时,**第一步就是把 [[aivive-design]] 喂进去**。

---

## 五、约定与偏好

- **语言**:用户使用中文为主,wiki 页面以中文为默认;但专有名词、合约地址、URL、英文原文保留原样。
- **敏感信息**:合约私钥、助记词、API Key 等永远不记录。公链合约地址、公开 URL、公开实体信息可正常记录。
- **版本管理**:本目录可初始化为 git 仓库以获得自动版本历史。每次 ingest/lint 之后建议 `git commit`。
- **不在 wiki 页面里堆原文**:wiki 是**消化过的**知识,原文档始终留在 `raw/`。如需引用长段原文,用链接而非复制。

---

## 六、当前项目简介

本仓库承载一个 Web3 项目的**重启孵化全流程资料**:

- **当前项目**:[[aivive|Aivive (AVV)]] — 2026-04-18 起正式启用的新品牌,Solana 上的 AI + 社交项目
- **历史项目**:[[red-horse|Red Horse (RH)]] — 同团队、同法律实体([[yu-network-srl]])下的前身项目,代币仍在 [[mexc]] 流通,不做迁移

[[index]] 为全量目录。时间线见 [log.md](./log.md)。

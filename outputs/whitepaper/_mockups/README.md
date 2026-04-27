# Whitepaper §4 Product Mockups

> 这个目录是给 §4 (`04-product.md`) 配截图用的工作区。
> **不会被 GitBook import**(下划线开头的目录默认被忽略)。

## 文件

- `product-mockups.html` — 3 个产品 mockup,纯 HTML/CSS,Aivive v0.2 品牌色

## 怎么用

### 1. 本地开浏览器

```bash
open /Users/ericc/Desktop/土豆/RedHorse/outputs/whitepaper/_mockups/product-mockups.html
```

或者直接在 Finder 里双击。

### 2. 截图 3 个 mockup

按住 `⌘ Shift 4` 然后空格键 → 鼠标变成相机 → 点击 mockup 卡片(浏览器里那个圆角白边框的区域)→ 自动截整块。

或者 `⌘ Shift 4` 拖框选。

### 3. 命名 + 存进 `images/`

```
outputs/whitepaper/images/feed-ui.png
outputs/whitepaper/images/studio-ui.png
outputs/whitepaper/images/tiers.png
```

(目录如果不存在就 `mkdir`)

### 4. 上 GitBook

**两种方式**:

**A. 在 GitBook 编辑器里手动插入**(推荐)
- import 完 markdown 后,在 GitBook web UI 编辑 §4 页面
- 在合适的位置 +号 → Image → Upload from computer → 选刚才的截图
- GitBook 会托管到自家 CDN

**B. 走 Git Sync**(等 GitHub 网络好了)
- 把 `outputs/whitepaper/images/` 一起 push
- 在 markdown 里写 `![Feed UI](images/feed-ui.png)`
- GitBook 自动渲染

## 建议插入位置

| Mockup | 截图建议 | 插入位置 |
|---|---|---|
| Feed UI | 1200×800 px | §4.5 "Why a Feed (Not a Chatbox)" 标题上方 |
| Studio UI | 1200×900 px | §4.4 "Three Generation Tiers" 表格上方 |
| Tier Comparison | 1200×500 px | §4.4 "Three Generation Tiers" 表格替换或下方 |

## 修改 mockup

直接改 `product-mockups.html`:
- 颜色:开头 `:root` 里的 token,改 `--aqua-500` 之类
- 文案:每个 `<div class="mockup">` 块里的文字
- 布局:CSS 在 `<style>` 标签里,grid / flex 都标了注释

改完保存,浏览器刷新就看到效果。

# Interactive Drama Script Generator
# 剧情演绎类脚本生成器

A single-page web tool that turns novels / interactive-fiction material into **short-video feed style interactive drama script fragments** — the "description line + choices + post-click plot" clickable-branch format used in interactive-fiction feed ads.

一个单页网页工具,把小说 / 互动剧情素材改编成**短视频信息流风格的互动短剧片段**——即互动小说信息流广告常用的「描述语 + 选项 + 点击后剧情」可点击分支结构。

You bring your own **Claude API key**; the page calls Claude directly from your browser. Nothing you type is stored on this site.

你使用**自己的 Claude 密钥**;网页在你的浏览器里直接调用 Claude。你输入的内容不会存在本站。

**Live site / 在线地址:** https://chenchang-7.github.io/juqing-tool/

---

## What it does / 它能做什么

Upload material (txt / docx / pdf) or paste text, describe what you want, and it generates one or more script versions in this fixed structure:

上传素材(txt / docx / pdf)或粘贴正文,写下你的需求,它会按下面这个固定结构生成一版或多版脚本:

```
# Version X | Selling point in one line / 版本X | 一句话卖点

### 1. Opening shot / 开头画面
[one high-impact action shot / 一句高冲击动作画面]

### 2. Description line / 描述语
「[identity + conflict + action, one sentence / 身份 + 冲突 + 动作,一句话]」

### 3. 【Your choice / 你的选择】
1. [short action option / 短动作选项]
2. [short action option / 短动作选项]

### 4. After clicking 【option】/ 点击【选项名】后
[5-8 lines: action feedback + short dialogue + character-contrast lines + escalation
 5-8句:动作反馈 + 短对白 + 角色反差台词 + 关系/危险升级]

### 5. Description line / 描述语
「[new suspense / relationship or danger escalation / 承接新悬念、关系升级或危险亲密]」

### 6. 【Your choice / 你的选择】
1. [push / counter / probe — 推进 / 反击 / 试探]
2. [dodge / defy / provoke — 躲开 / 嘴硬 / 挑衅]
```

Good for generating multiple versions by different love interests, character relationships, or plot hooks.

适合按不同攻略对象、人物关系或剧情钩子,一次生成多版可点击分支。

### Edit any part with your mouse / 选中即改

After generating, **select any sentence** in the result and right-click (or click the floating "✎ 修改选中" button) to open a small window, type an instruction (e.g. "make this more tense", "give a bolder option"), and the AI rewrites **only the version your selection belongs to** — other versions stay untouched. It sees that whole version as context, so it can also smooth out transitions, not just the selected line. The result is shown side-by-side (original left, revised right); keep it with **采纳** or drop it with **放弃**.

生成后,在结果里**用鼠标划选任意一句话**,右键(或点浮出的「✎ 修改选中」按钮)弹出小窗,写下修改指令(如「改得更紧张」「换个更狠的选项」),AI 只会重写**你选中片段所在的那一版**,其它版本保持不变。它会带上整版上下文,所以不只是改那一句,还能顺带理顺衔接。改完左右对比(左原版、右改后),满意点**采纳**,不满意点**放弃**。

---

## How to use / 怎么用

1. Open the live site. / 打开在线地址。
2. Enter your Claude API key (starts with `sk-ant-`). Tick "remember" to keep it in your own browser only.
   填入你的 Claude 密钥(以 `sk-ant-` 开头)。勾选「记住密钥」,只会存在你自己的浏览器里。
3. Pick a model (Opus = highest quality, Sonnet = fast, Haiku = cheapest).
   选择模型(Opus 质量最高、Sonnet 快、Haiku 最省)。
4. Upload material files or paste the source text. / 上传素材文件或粘贴正文。
5. Write your requirements (optional) and click **Generate**. / 写下需求(可选),点**开始生成**。
6. (Optional) Select any sentence in the result → right-click → type an instruction to refine just that version. / (可选)在结果里划选任意一句 → 右键 → 输入指令,只精修那一版。

The key is stored only in your browser's localStorage and is sent directly to Anthropic's API. It never touches this site's host.

密钥只存在你浏览器的 localStorage,直接发给 Anthropic 官方接口,不经过本站服务器。

---

## Privacy / 隐私

- **This site (GitHub Pages):** static only. It does not store your prompts or results. Your key/model choice live in your browser's localStorage.
  **本站(GitHub Pages):** 纯静态,不存储你的指令或结果。密钥和模型选择只存在你自己浏览器里。
- **Anthropic:** your requests go to Claude's API and are subject to Anthropic's data-retention policy.
  **Anthropic:** 你的请求会发到 Claude 接口,受 Anthropic 的数据留存政策约束。

Don't paste anything you wouldn't send to a third-party API.

不要粘贴任何你不愿发给第三方接口的敏感内容。

---

## Tech / 技术

Zero-build single HTML file. Uses the Anthropic Messages API with streaming and prompt caching, plus `marked.js` (markdown), `mammoth.js` (docx), and `pdf.js` (pdf) from CDN.

零构建单 HTML 文件。使用 Anthropic Messages API(流式 + 提示缓存),并通过 CDN 引入 `marked.js`(markdown)、`mammoth.js`(docx)、`pdf.js`(pdf)。

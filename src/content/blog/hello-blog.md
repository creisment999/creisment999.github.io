---
title: '第一篇：如何用这个博客写笔记'
description: '从新建 Markdown 到本地预览、推送到 GitHub Pages 的最短路径。'
pubDate: 'Aug 29 2026'
heroImage: '../../assets/blog-placeholder-1.jpg'
tags: ['博客', '入门']
---

欢迎。这篇文章演示你以后写笔记的基本流程。

## 新建一篇文章

在 `src/content/blog/` 下新建一个 `.md` 文件，例如 `ospf-lab-01.md`，头部写成：

```markdown
---
title: 'OSPF 单区域实验笔记'
description: 'GNS3 里搭一个单区域 OSPF，记录邻居建立与路由表。'
pubDate: 'Aug 30 2026'
tags: ['网络工程', 'OSPF']
---

正文从这里开始……
```

文件名会变成文章 URL，例如：`/blog/ospf-lab-01/`。

## 本地预览

```bash
npm run dev
```

浏览器打开终端提示的地址（一般是 `http://localhost:4321`），改完保存会自动刷新。

## 发布

把改动提交并推送到 `main` 分支。GitHub Actions 会自动构建并部署到 GitHub Pages。

写作建议：标题说清楚主题，正文写「目标 → 步骤 → 结果 → 踩坑」，代码块和命令尽量可复制。

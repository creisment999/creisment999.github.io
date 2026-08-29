# 学习笔记 · GitHub 技术博客

基于 [Astro](https://astro.build/) 官方 Blog 模板的简约技术博客，用于记录**网络工程**与**编程**学习内容。托管在 GitHub Pages，免费、纯静态。

访问地址：`https://crisment999.github.io`

---

## 发布到 GitHub Pages

仓库：`https://github.com/crisment999/crisment999.github.io`

### 1. 推送代码（若尚未推送）

```bash
git init
git add .
git commit -m "init: astro tech blog"
git branch -M main
git remote add origin https://github.com/crisment999/crisment999.github.io.git
git push -u origin main
```

### 2. 打开 GitHub Pages

仓库页面 → **Settings** → **Pages**：

1. **Source** 选 **GitHub Actions**
2. 等待 Actions 里的 `Deploy to GitHub Pages` 跑完（绿色勾）
3. 打开 `https://crisment999.github.io`

若第一次部署失败，多半是 Pages 源还没切到 GitHub Actions，改完后重新跑一次 workflow 即可。

---

## 日常写文章

1. 在 `src/content/blog/` 新建 `xxx.md`
2. 写好 frontmatter（标题、描述、日期、标签）
3. 本地预览：`npm run dev`
4. `git add/commit/push` → 自动上线

示例 frontmatter：

```markdown
---
title: '文章标题'
description: '一句话摘要'
pubDate: 'Aug 30 2026'
tags: ['网络工程', 'OSPF']
---
```

---

## 本地命令

| 命令 | 作用 |
| --- | --- |
| `npm install` | 安装依赖（已配置 npmmirror） |
| `npm run dev` | 本地开发预览 |
| `npm run build` | 生产构建，输出到 `dist/` |
| `npm run preview` | 预览构建结果 |

若 `npm install` 很慢或失败，可换源：

```bash
npm config set registry https://registry.npmmirror.com
npm install
```

---

## 项目结构（常用部分）

```text
src/
  content/blog/     # 文章（Markdown）
  pages/            # 页面路由
  components/       # 页头、页脚等
  consts.ts         # 站点标题、GitHub 用户名
astro.config.mjs    # 站点 URL 等配置
.github/workflows/  # GitHub Pages 自动部署
```

---

## 已替你完成的部分

- Astro Blog 模板初始化与依赖安装
- 中文首页 / 关于页 / 导航
- 3 篇示例文章（博客用法、TCP 握手、Python 探测脚本）
- 文章 `tags` 字段
- GitHub Actions 自动部署到 Pages

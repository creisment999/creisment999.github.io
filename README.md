# Tech Notes

Live site: https://creisment999.github.io

## Add a new post

1. Create a Markdown file in `src/content/blog/` (e.g. `my-topic.md`)
2. Add frontmatter, then write the body:

```markdown
---
title: 'Post title'
description: 'One-line summary'
pubDate: 'Aug 30 2026'
tags: ['networking']
---

Your content here.
```

3. Preview: `npm run dev` → http://localhost:4321
4. Publish: `git add` → `git commit` → `git push` to `main`

The filename is the URL slug: `my-topic.md` → `/blog/my-topic/`.

## Turn the website on / off

Open: https://github.com/creisment999/creisment999.github.io/settings/pages

| Action | What to do |
| --- | --- |
| **On** | Source → **GitHub Actions**. Wait for `Deploy to GitHub Pages` to succeed. |
| **Off** | Change Source away from GitHub Actions, or use **Unpublish** if shown. |

## Commands

| Command | Description |
| --- | --- |
| `npm install` | Install dependencies |
| `npm run dev` | Local preview |
| `npm run build` | Production build → `dist/` |
| `npm run preview` | Preview the production build |

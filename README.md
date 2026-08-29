# Tech Notes

Personal blog for networking and programming notes. Live at https://creisment999.github.io

## Write a post

1. Create a Markdown file in `src/content/blog/`
2. Add frontmatter, then write the body
3. Preview locally with `npm run dev`
4. Push to `main` — GitHub Actions deploys automatically

```markdown
---
title: 'Post title'
description: 'One-line summary'
pubDate: 'Aug 30 2026'
tags: ['networking', 'OSPF']
---

Your content here.
```

The filename becomes the URL slug, e.g. `ospf-lab-01.md` → `/blog/ospf-lab-01/`.

## Commands

| Command | Description |
| --- | --- |
| `npm install` | Install dependencies |
| `npm run dev` | Local preview |
| `npm run build` | Production build → `dist/` |
| `npm run preview` | Preview the production build |

If `npm install` is slow:

```bash
npm config set registry https://registry.npmmirror.com
npm install
```

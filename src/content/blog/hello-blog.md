---
title: 'Getting started: how to write notes here'
description: 'Shortest path from a new Markdown file to a live GitHub Pages post.'
pubDate: 'Aug 29 2026'
heroImage: '../../assets/blog-placeholder-1.jpg'
tags: ['blog', 'getting-started']
---

Welcome. This post shows the basic workflow for writing notes on this site.

## Create a post

Add a `.md` file under `src/content/blog/`, for example `ospf-lab-01.md`:

```markdown
---
title: 'OSPF single-area lab notes'
description: 'Build a single-area OSPF topology in GNS3 and record neighbor state and routes.'
pubDate: 'Aug 30 2026'
tags: ['networking', 'OSPF']
---

Start writing here...
```

The filename becomes the URL, e.g. `/blog/ospf-lab-01/`.

## Preview locally

```bash
npm run dev
```

Open the URL printed in the terminal (usually `http://localhost:4321`). Saves reload automatically.

## Publish

Commit and push to `main`. GitHub Actions builds and deploys to GitHub Pages.

Writing tip: make the title specific, and structure the body as goal → steps → result → pitfalls. Keep commands copy-pasteable.

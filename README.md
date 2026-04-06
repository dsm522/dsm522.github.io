# dsm522.github.io

Personal website for Sanjiv Ranjan.

- **Live site:** https://dsm522.github.io/
- **Framework:** Hugo
- **Theme:** custom in-repo theme (`themes/sr-theme`)
- **Deploy:** GitHub Pages via GitHub Actions

For the full operating notes, edit flow, troubleshooting, and publishing details, see:

- [`RUNBOOK.md`](./RUNBOOK.md)

## Local preview

```bash
cd /home/sanjiv/sanjiv.me
hugo server
```

Open:
- `http://localhost:1313/`

## Build locally

```bash
cd /home/sanjiv/sanjiv.me
hugo --minify
```

## Publish changes

```bash
cd /home/sanjiv/sanjiv.me
git add .
git commit -m "Update website"
git push
```

## Main folders

```text
content/               # pages and blog posts
static/images/blog/    # blog images
themes/sr-theme/       # theme templates, CSS, JS
.github/workflows/     # deploy workflow
```

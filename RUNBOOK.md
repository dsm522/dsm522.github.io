# dsm522.github.io — Runbook

This is the runbook for Sanjiv's personal website.

## At a glance

- **Repo:** `git@github.com:dsm522/dsm522.github.io.git`
- **Live site:** `https://dsm522.github.io/`
- **Local path:** `/home/sanjiv/sanjiv.me`
- **Framework:** Hugo
- **Theme:** `themes/sr-theme`
- **Deploy:** GitHub Pages via GitHub Actions

This repo is the source of truth. Not the OpenClaw workspace copy.

## Structure

```text
/home/sanjiv/sanjiv.me
├── .github/workflows/hugo.yml      # deploy workflow
├── hugo.toml                       # site config
├── content/
│   ├── _index.md                   # homepage front matter
│   └── blog/                       # blog posts
├── static/images/blog/             # blog images
├── themes/sr-theme/
│   ├── layouts/                    # templates
│   └── static/                     # CSS / JS
└── public/                         # generated output
```

## Standard workflow

### Preview locally

```bash
cd /home/sanjiv/sanjiv.me
hugo server
```

Preview at:
- `http://localhost:1313/`

### Build locally

```bash
cd /home/sanjiv/sanjiv.me
hugo --minify
```

### Publish

```bash
cd /home/sanjiv/sanjiv.me
git add .
git commit -m "Describe the change"
git push
```

A push triggers `.github/workflows/hugo.yml`, which builds the site and publishes it to GitHub Pages.

## Blog posts

### Create a post

```bash
cd /home/sanjiv/sanjiv.me
hugo new content blog/my-post-title.md
```

Edit the new file in `content/blog/`.

### Front matter

```yaml
---
title: "Your Post Title"
date: 2026-04-06
description: "Short description for previews and SEO."
image: "/images/blog/your-image.jpg"
---
```

### Images

Put blog images in:

```text
static/images/blog/
```

And reference them like this:

```yaml
image: "/images/blog/example.jpg"
```

## LinkedIn-to-blog workflow

If a post comes from LinkedIn:
1. copy/adapt the text into `content/blog/`
2. pull the matching published image
3. save it into `static/images/blog/`
4. add the `image:` field
5. preview locally
6. commit and push

If the image needs to match LinkedIn exactly, use the actual published asset, not a screenshot or a smaller preview.

## Common edit points

### Homepage copy
- `content/_index.md`
- `themes/sr-theme/layouts/index.html`

### Navigation
- `hugo.toml`

### Footer / contact
- `themes/sr-theme/layouts/partials/footer.html`

### Styling
- `themes/sr-theme/static/css/main.css`

### JavaScript
- `themes/sr-theme/static/js/main.js`

## Pages config

Expected setup:
- repo name: `dsm522.github.io`
- Pages source: **GitHub Actions**
- live URL: `https://dsm522.github.io/`
- HTTPS: on

Production build command in the workflow:

```bash
hugo --minify --baseURL "https://dsm522.github.io/"
```

## Troubleshooting

### Changes pushed, but live site hasn't updated

Check Actions:
- `https://github.com/dsm522/dsm522.github.io/actions`

If needed, trigger a fresh deploy:

```bash
cd /home/sanjiv/sanjiv.me
git commit --allow-empty -m "Trigger Pages deploy"
git push
```

### GitHub Pages is showing repo files instead of the site

Pages has probably slipped back to **Deploy from a branch**.

Fix:
- go to **Repo Settings → Pages**
- set **Source** to **GitHub Actions**
- push again if needed

### Image works locally, but not live

Check:
- the file exists in `static/images/blog/`
- the front matter path starts with `/images/blog/`
- the change was committed and pushed
- the deploy completed after the image was added

### Wrong LinkedIn image variant

LinkedIn exposes multiple versions of the same image.
If the website image is wrong:
- re-pull the exact published asset
- replace the file in `static/images/blog/`
- commit and push

### Local preview looks stale

```bash
pkill -f "hugo server" || true
cd /home/sanjiv/sanjiv.me
hugo server
```

## Working rules

- edit in `/home/sanjiv/sanjiv.me`
- treat this repo as the source of truth
- preview before pushing if layout, nav, or images changed
- use clear commit messages
- keep LinkedIn-derived posts sounding natural, not overworked

## Quick commands

### Preview

```bash
cd /home/sanjiv/sanjiv.me
hugo server
```

### Build

```bash
cd /home/sanjiv/sanjiv.me
hugo --minify
```

### Publish

```bash
cd /home/sanjiv/sanjiv.me
git add .
git commit -m "Update website"
git push
```

### Check remote

```bash
cd /home/sanjiv/sanjiv.me
git remote -v
```

Expected remote:

```text
git@github.com:dsm522/dsm522.github.io.git
```

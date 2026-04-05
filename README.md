# sanjivranjanuk.github.io

Personal website for Sanjiv Ranjan — AI Adoption & Transformation Leader.

Built with [Hugo](https://gohugo.io/) using a custom self-contained theme (`sr-theme`). No external theme dependencies or git submodules.

---

## Prerequisites

Hugo extended v0.100+. If not installed:

```bash
# Option A: Download binary (no sudo needed)
curl -L https://github.com/gohugoio/hugo/releases/download/v0.142.0/hugo_extended_0.142.0_linux-amd64.tar.gz | tar xz
mkdir -p ~/.local/bin && mv hugo ~/.local/bin/
export PATH=$PATH:~/.local/bin

# Option B: Snap (Linux)
sudo snap install hugo --channel=extended

# Option C: Homebrew (macOS)
brew install hugo
```

---

## Local Development

```bash
cd website
hugo server
```

Visit http://localhost:1313

With draft posts:
```bash
hugo server --buildDrafts
```

---

## Build for Production

```bash
hugo --minify
```

Output goes to `public/`. This is what you deploy.

---

## Deploy to GitHub Pages

1. Create a repo named `<yourusername>.github.io`
2. Push this `website/` directory (or the whole repo)
3. In repo Settings → Pages → Source: **GitHub Actions**
4. Add `.github/workflows/hugo.yml`:

```yaml
name: Deploy Hugo site

on:
  push:
    branches: [main]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Setup Hugo
        uses: peaceiris/actions-hugo@v3
        with:
          hugo-version: '0.142.0'
          extended: true
      - name: Build
        run: hugo --minify
      - name: Deploy
        uses: peaceiris/actions-gh-pages@v4
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./public
```

Update `baseURL` in `hugo.toml` to your actual URL before pushing.

---

## Deploy to Netlify

1. Push to GitHub
2. Connect repo to Netlify
3. Build command: `hugo --minify`
4. Publish directory: `public`
5. Set environment variable: `HUGO_VERSION = 0.142.0`

Or use the Netlify CLI:
```bash
npm install -g netlify-cli
hugo --minify
netlify deploy --dir=public --prod
```

---

## Adding Blog Posts

```bash
hugo new content blog/my-post-title.md
```

Edit the file in `content/blog/`. Set `draft: false` when ready to publish.

Front matter format:
```yaml
---
title: "Your Post Title"
date: 2026-02-26
description: "A short description for SEO and preview cards."
---
```

---

## Structure

```
website/
├── hugo.toml                 # Site config
├── content/
│   ├── _index.md             # Homepage
│   └── blog/                 # Blog posts (Markdown)
├── themes/sr-theme/
│   ├── layouts/
│   │   ├── _default/         # Base templates
│   │   ├── blog/             # Blog-specific templates
│   │   ├── partials/         # Nav, head, footer
│   │   └── index.html        # Homepage template
│   └── static/
│       ├── css/main.css      # All styles
│       └── js/main.js        # Scroll, mobile nav
└── public/                   # Build output (git-ignored)
```

---

## Customisation

- **Colours / fonts**: Edit CSS variables at the top of `themes/sr-theme/static/css/main.css`
- **Nav links**: Edit `[menus]` in `hugo.toml`
- **Homepage sections**: Edit `themes/sr-theme/layouts/index.html`
- **Contact info**: Edit `themes/sr-theme/layouts/partials/footer.html`

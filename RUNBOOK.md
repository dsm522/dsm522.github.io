# dsm522.github.io — Runbook

This is the operating note for Sanjiv's personal website.

## What this site is

- **Repo:** `git@github.com:dsm522/dsm522.github.io.git`
- **Live URL:** `https://dsm522.github.io/`
- **Local repo path:** `/home/sanjiv/sanjiv.me`
- **Framework:** Hugo
- **Theme:** custom in-repo theme, `themes/sr-theme`
- **Deploy method:** GitHub Pages via GitHub Actions

This is now the canonical personal-site repo. It is separate from the OpenClaw workspace.

## Key files and folders

```text
/home/sanjiv/sanjiv.me
├── .github/workflows/hugo.yml      # GitHub Pages deploy workflow
├── hugo.toml                       # site config
├── content/
│   ├── _index.md                   # homepage front matter
│   └── blog/                       # blog posts
├── static/
│   └── images/blog/                # blog images
├── themes/sr-theme/
│   ├── layouts/                    # templates
│   └── static/                     # theme CSS/JS
└── public/                         # generated output, local only
```

## Normal edit flow

### 1. Start local preview

```bash
cd /home/sanjiv/sanjiv.me
hugo server
```

Preview at:
- `http://localhost:1313/`

If Hugo isn't installed:

```bash
curl -L https://github.com/gohugoio/hugo/releases/download/v0.142.0/hugo_extended_0.142.0_linux-amd64.tar.gz | tar xz
mkdir -p ~/.local/bin
mv hugo ~/.local/bin/
export PATH=$PATH:~/.local/bin
```

## Publishing changes

For this site, publishing is just git push.

```bash
cd /home/sanjiv/sanjiv.me
git status
git add .
git commit -m "Describe the change"
git push
```

What happens next:
- GitHub Actions runs `.github/workflows/hugo.yml`
- Hugo builds the site
- GitHub Pages publishes it to `https://dsm522.github.io/`

## Build workflow

Current deploy workflow file:
- `.github/workflows/hugo.yml`

Current production build command inside the workflow:

```bash
hugo --minify --baseURL "https://dsm522.github.io/"
```

That means the workflow controls the production base URL even if local testing uses localhost.

## Blog posts

### Create a new post

```bash
cd /home/sanjiv/sanjiv.me
hugo new content blog/my-post-title.md
```

Then edit the new file in `content/blog/`.

### Recommended front matter

```yaml
---
title: "Your Post Title"
date: 2026-04-06
description: "Short description for previews and SEO."
image: "/images/blog/your-image.jpg"
---
```

### Where images go

Put blog images here:

```text
static/images/blog/
```

And reference them like this in front matter:

```yaml
image: "/images/blog/example.jpg"
```

## If a post comes from LinkedIn

The cleanest flow is:
1. Copy the post into `content/blog/`
2. Pull the matching LinkedIn image
3. Save it to `static/images/blog/`
4. Add the `image:` field in front matter
5. Preview locally
6. Commit and push

Important: if matching the LinkedIn image exactly matters, grab the actual published image from LinkedIn rather than using a screenshot or a smaller preview version.

## Homepage and site structure edits

### Homepage copy
- `content/_index.md`
- `themes/sr-theme/layouts/index.html`

### Navigation / menus
- `hugo.toml`

### Footer / contact details
- `themes/sr-theme/layouts/partials/footer.html`

### Global styles
- `themes/sr-theme/static/css/main.css`

### Global JS
- `themes/sr-theme/static/js/main.js`

## Local build

To generate the static site locally:

```bash
cd /home/sanjiv/sanjiv.me
hugo --minify
```

Output goes to:
- `public/`

That folder is build output. Treat source files as the real thing.

## GitHub Pages settings

Expected configuration:
- **Repo name:** `dsm522.github.io`
- **Pages source:** `GitHub Actions`
- **Live URL:** `https://dsm522.github.io/`
- **HTTPS:** on

If the site suddenly starts serving raw repo content or looks wrong, the first thing to check is whether Pages has slipped back to **Deploy from a branch**.

## Troubleshooting

### 1. Site is live, but changes haven't appeared yet

Check the latest GitHub Actions runs:
- `https://github.com/dsm522/dsm522.github.io/actions`

If needed, trigger a new deploy:

```bash
cd /home/sanjiv/sanjiv.me
git commit --allow-empty -m "Trigger Pages deploy"
git push
```

### 2. GitHub Pages shows repo files instead of the Hugo site

Cause: Pages is probably using branch deploy instead of the Hugo workflow.

Fix:
- go to **Repo Settings → Pages**
- set **Source** to **GitHub Actions**
- push again if needed

### 3. Image shows locally but not on the live site

Check all three:
- file exists in `static/images/blog/`
- front matter path starts with `/images/blog/...`
- change has been committed and pushed

Also check that the deploy completed after the image was added.

### 4. Wrong image variant from LinkedIn

LinkedIn often exposes multiple versions of the same image.
If the website image doesn't match the published post properly:
- re-pull the exact published asset
- replace the file in `static/images/blog/`
- commit and push

### 5. Local preview looks stale

Restart Hugo:

```bash
pkill -f "hugo server" || true
cd /home/sanjiv/sanjiv.me
hugo server
```

## Good operating habits

- Keep content edits in this repo, not in the workspace copy
- Treat `/home/sanjiv/sanjiv.me` as the source of truth
- Use clear commit messages
- Preview before pushing if the change affects layout, images, or navigation
- If a post is adapted from LinkedIn, keep the tone natural and reflective, not over-polished

## Quick commands

### Preview locally

```bash
cd /home/sanjiv/sanjiv.me
hugo server
```

### Build locally

```bash
cd /home/sanjiv/sanjiv.me
hugo --minify
```

### Publish changes

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

# Docker DevTools Documentation

This repository contains the source for the **Docker DevTools** documentation site, built with [Jekyll](https://jekyllrb.com/) and the [just-the-docs](https://just-the-docs.com/) theme, and deployed to GitHub Pages.

📖 Live site: https://willhallonline.github.io/docker-devtools.github.io/

The documentation covers [`docker-devtools-aliases`](https://github.com/willhallonline/docker-devtools-aliases) — a set of shell aliases that run common developer tools (linters, formatters, package managers) inside Docker containers, for both bash/zsh and PowerShell.

## Local development

```bash
bundle install
bundle exec jekyll serve
```

Then open http://localhost:4000/docker-devtools.github.io/ in your browser. Jekyll will rebuild automatically as you edit files.

## Deployment

Pushes to `master` are built and deployed automatically to GitHub Pages via the workflow in [`.github/workflows/pages.yml`](.github/workflows/pages.yml), using GitHub's official `actions/configure-pages`, `actions/upload-pages-artifact`, and `actions/deploy-pages` actions.

To enable this the first time, in the repository **Settings → Pages**, set the **Source** to **GitHub Actions**.

## Content structure

| File | Section |
|------|---------|
| `index.md` | Home |
| `installation.md` | Installation |
| `tools.md` | Available tools |
| `configuration.md` | Runtime configuration |
| `testing.md` | Testing |
| `troubleshooting.md` | Troubleshooting |

Content is sourced from and kept in sync with the [`docker-devtools-aliases`](https://github.com/willhallonline/docker-devtools-aliases) README.

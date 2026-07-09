---
title: Available tools
layout: default
nav_order: 3
description: "Full list of Docker DevTools aliases for JavaScript, PHP, Python, images, and AI tooling."
permalink: /tools
---

# Available tools
{: .no_toc }

All aliases mount the **current working directory** into the container and run the tool there. Arguments after the alias are forwarded directly to the tool.
{: .fs-6 .fw-300 }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## JavaScript / CSS

| Alias | Tool | Image |
|-------|------|-------|
| `stylelint-docker` | Stylelint CSS linter (community image) | `solutiondrive/stylelint:latest` |
| `eslint-docker` | ESLint (community image) | `pipelinecomponents/eslint:latest` |
| `node-docker` | Node.js REPL / scripts | `node:22-alpine` |
| `npm-docker` | npm | `node:22-alpine` |
| `yarn-docker` | Yarn | `node:22-alpine` |
| `pnpm-docker` | pnpm | `node:22-alpine` |
| `node-bash-docker` | Interactive bash in Node container | `node:22-alpine` |

## PHP

| Alias | Tool | Image |
|-------|------|-------|
| `composer-docker` | Composer package manager (official image) | `composer:latest` |
| `php-docker` | PHP CLI / scripts | `php:8.4-alpine` |
| `phpcs-generic` / `phpcbf-generic` | PHP_CodeSniffer (generic, community image) | `texthtml/phpcs:latest` |
| `phpcs-drupal` / `phpcbf-drupal` | PHP_CodeSniffer (Drupal standard) | `texthtml/phpcs:latest` |
| `phpcs-wordpress` / `phpcbf-wordpress` | PHP_CodeSniffer (WordPress standard) | `texthtml/phpcs:latest` |
| `phpcs-cakephp` / `phpcbf-cakephp` | PHP_CodeSniffer (CakePHP standard) | `texthtml/phpcs:latest` |
| `phpcs-yii` / `phpcbf-yii` | PHP_CodeSniffer (Yii standard) | `texthtml/phpcs:latest` |
| `phpcs-laravel` / `phpcbf-laravel` | PHP_CodeSniffer (Laravel standard) | `texthtml/phpcs:latest` |

{: .note }
`phpcs-d` and `phpcbf-d` (Drupal, local) are thin wrappers around `~/.composer/vendor/bin/phpcs` and require a local Composer-installed copy of `drupal/coder`. They do **not** use Docker. All `phpcs-*` / `phpcbf-*` Docker aliases share a single community-maintained image (`texthtml/phpcs`, actively updated with PHP_CodeSniffer 4.0.1). Configure framework-specific standards via a `.phpcs.xml` in your project root, or pass `--standard=...` directly.

## Python

| Alias | Tool | Image |
|-------|------|-------|
| `python-docker` | Python REPL / scripts | `python:alpine` |
| `pip-docker` | pip package manager | `python:alpine` |
| `python-bash-docker` | Interactive shell in Python container | `python:alpine` |
| `black-docker` | Black code formatter | `pyfound/black:latest_release` |
| `flake8-docker` | Flake8 style/lint checker (PEP 8) | `alpine/flake8:latest` |
| `pylint-docker` | Pylint static analysis | `cytopia/pylint:latest` |
| `mypy-docker` | Mypy static type checker | `cytopia/mypy:latest` |
| `bandit-docker` | Bandit security linter | `cytopia/bandit:latest` |

## Images

The `images/docker-image-devtools.sh` file contains image-conversion, resizing, and optimisation aliases. This file is **not** sourced automatically — add it explicitly if you need it:

```bash
source ~/.docker-devtools/docker-devtools.sh
source ~/.docker-devtools/images/docker-image-devtools.sh
```

In PowerShell:

```powershell
. "$HOME/.docker-devtools/docker-devtools.ps1"
. "$HOME/.docker-devtools/images/docker-image-devtools.ps1"
```

| Alias | Tool | Image |
|-------|------|-------|
| `jpegtran-docker` | JPEG lossless transformation (mozjpeg) | `datawraith/mozjpeg` |
| `magick-docker` / `convert-docker` | ImageMagick — conversion & resizing | `dpokidov/imagemagick:latest` |
| `mogrify-docker` | ImageMagick — in-place batch conversion/resize | `dpokidov/imagemagick:latest` |
| `identify-docker` | ImageMagick — image metadata/info | `dpokidov/imagemagick:latest` |
| `vipsthumbnail-docker` | libvips — fast, low-memory thumbnailing/resizing | `marcbachmann/libvips:latest` |
| `cwebp-docker` / `dwebp-docker` | WebP encode/decode | `takecy/webp:latest` |

```bash
# Resize an image with ImageMagick
magick-docker input.jpg -resize 50% output.jpg

# Batch-resize and reformat in place
mogrify-docker -resize 800x600 -format png *.jpg

# Generate a fast thumbnail with libvips
vipsthumbnail-docker input.jpg --size 200x200 -o thumb.jpg

# Convert to/from WebP
cwebp-docker input.png -o output.webp
dwebp-docker output.webp -o roundtrip.png
```

## AI tools

The `ai/docker-ai-devtools.sh` file contains aliases for AI-powered CLI tools. This file is **not** sourced automatically — add it explicitly if you need it:

```bash
source ~/.docker-devtools/docker-devtools.sh
source ~/.docker-devtools/ai/docker-ai-devtools.sh
```

| Alias | Tool | Image |
|-------|------|-------|
| `markitdown-docker` | [MarkItDown](https://github.com/microsoft/markitdown) — converts PDFs, Office docs, images, audio, HTML, etc. to Markdown for LLMs | `python:3.13-slim` (installs `markitdown` at runtime) |
| `llm-docker` | [llm](https://llm.datasette.io) — Simon Willison's CLI for prompting/piping data through LLMs | `python:3.13-slim` (installs `llm` at runtime) |
| `openwiki-docker` | [OpenWiki](https://github.com/langchain-ai/openwiki) — generates and maintains agent-readable docs for a codebase | `node:22-alpine` (via `npx`) |
| `aider-docker` | [Aider](https://aider.chat) — AI pair-programming CLI that edits files and commits changes in your repo | `paulgauthier/aider-full` |

{: .note }
`markitdown-docker` and `llm-docker` have no official pre-built image, so they `pip install` the package into a fresh `python:3.13-slim` container on every run (a few extra seconds per invocation). Most of these tools call an LLM provider and need an API key — pass it through with `DOCKER_DEVTOOLS_EXTRA_ARGS`, e.g. `DOCKER_DEVTOOLS_EXTRA_ARGS="-e OPENAI_API_KEY" aider-docker`.

```bash
# Convert a PDF to Markdown
markitdown-docker report.pdf > report.md

# Ask an LLM about piped input
cat notes.txt | llm-docker "Summarize this"

# Generate docs for the current repo
openwiki-docker --init

# Let Aider edit a file with AI assistance
DOCKER_DEVTOOLS_EXTRA_ARGS="-e OPENAI_API_KEY" aider-docker some_file.py
```

## Usage examples

```bash
# Lint a CSS file
stylelint-docker bad.css

# Lint all JS files in the current directory
eslint-docker .

# Run Composer install
composer-docker install

# Check PHP code against Drupal standards
phpcs-drupal src/

# Fix automatically with PHP Code Beautifier
phpcbf-drupal src/

# Run a Node.js script
node-docker script.js

# Install npm dependencies
npm-docker install
```

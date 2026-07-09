---
title: Configuration
layout: default
nav_order: 4
description: "Environment variables and options for tuning Docker DevTools container behaviour."
permalink: /configuration
---

# Runtime configuration
{: .no_toc }

Three environment variables let you adjust container behaviour without modifying aliases.
{: .fs-6 .fw-300 }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## `DOCKER_DEVTOOLS_TTY`

Controls whether `-it` (interactive + TTY) is passed to `docker run`.

| Value | Behaviour |
|-------|-----------|
| `always` *(default)* | Always pass `-it` |
| `auto` | Pass `-it` only when stdin **and** stdout are connected to a terminal |
| `never` | Never pass `-it` (safe for scripts and CI) |

```bash
# Disable TTY for use in a CI pipeline or script
DOCKER_DEVTOOLS_TTY=never phpcs-generic src/
```

## `DOCKER_DEVTOOLS_MAP_HOST_USER`

When set to a truthy value (`true`, `1`, `yes`, `on`), adds `--user $(id -u):$(id -g)` so files written by the container are owned by the current host user instead of `root`.

```bash
DOCKER_DEVTOOLS_MAP_HOST_USER=true composer-docker install
```

Accepts: `true`, `1`, `yes`, `on` (enable) or `false`, `0`, `no`, `off`, empty (disable — default).

## `DOCKER_DEVTOOLS_EXTRA_ARGS`

A space-separated list of extra flags appended to `docker run` **before** the image name. Useful for network, registry, or pull-policy overrides.

```bash
# Force a fresh pull and use the host network
DOCKER_DEVTOOLS_EXTRA_ARGS="--pull always --network host" stylelint-docker .
```

You can export these variables in your shell profile to apply them globally:

```bash
export DOCKER_DEVTOOLS_TTY=auto
export DOCKER_DEVTOOLS_MAP_HOST_USER=true
```

## `--entrypoint <name>` (alias definitions)

Some multi-tool images (e.g. ImageMagick, libvips, WebP) bake in a default entrypoint that doesn't match every binary the image ships. Alias authors can override it by passing `--entrypoint <name>` immediately after the image in a `docker_alias` call:

```bash
alias mogrify-docker="docker_alias /imgs dpokidov/imagemagick:latest --entrypoint mogrify"
```

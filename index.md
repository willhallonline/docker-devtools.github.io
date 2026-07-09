---
title: Home
layout: home
nav_order: 1
description: "Docker DevTools — run common developer tools inside Docker containers via simple shell aliases."
permalink: /
---

# Docker DevTools
{: .fs-9 }

Docker DevTools provides a set of shell aliases that run common developer tools — linters, formatters, package managers — inside Docker containers. No local language runtimes required.
{: .fs-6 .fw-300 }

[Get started now](installation){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 }
[View it on GitHub](https://github.com/willhallonline/docker-devtools-aliases){: .btn .fs-5 .mb-4 .mb-md-0 }

---

## Get it fast

```bash
git clone https://github.com/willhallonline/docker-devtools-aliases.git ~/.docker-devtools
```

## How do you manage your dependencies?

**Docker DevTools** comes straight out of a need for more dependencies, more tools and more control. If you have been around web development for the past 15+ years, you will have seen an explosion of different tools, frameworks and practices. Most make your projects better, however they come with extra complexity.

Even simple applications end up depending on multiple coding standards — PHP coding standards for WordPress, Drupal, Yii, CakePHP or plain PSR-12; JavaScript standards with ESLint (Standard or Airbnb); CSS standards with Stylelint. All of these require configuration and installation.

By running these tools in Docker containers, linting and fixing your code becomes simple, without bloating your local machine with hundreds of dependencies or fighting version mismatches between projects.

Follow the [quick start](installation) to get up and running. Use it as part of your local workflow, your CI pipeline, or both — for the *best code, all the time*.

## What's inside

| Area | What you get |
|:--|:--|
| [Installation](installation) | Clone-and-source setup for bash/zsh and PowerShell |
| [Available tools](tools) | JavaScript/CSS, PHP, Python, image, and AI tool aliases |
| [Configuration](configuration) | Environment variables to control TTY, file ownership, and extra Docker args |
| [Testing](testing) | Running the bundled bash and PowerShell test harnesses |
| [Troubleshooting](troubleshooting) | Fixes for the most common setup issues |

## Why Docker DevTools?

- **Zero local installs** — no Node, PHP, Python, or ImageMagick required on your host.
- **Consistent versions** — every teammate and every CI run uses the exact same tool version.
- **Cross-platform** — matching bash and PowerShell implementations, so it works the same on Linux, macOS, and Windows.
- **Drop-in aliases** — `eslint-docker`, `phpcs-drupal`, `python-docker`, and friends behave like the real CLI, just running in a container.

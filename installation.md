---
title: Installation
layout: default
nav_order: 2
description: "How to install Docker DevTools aliases for bash, zsh, and PowerShell."
permalink: /installation
---

# Installation
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Prerequisites

| Requirement | Notes |
|-------------|-------|
| **Docker** | Must be installed and in `PATH`. [Get Docker](https://docs.docker.com/get-docker/) |
| **Bash 4+** or **zsh** | The wrapper uses bash arrays; macOS ships bash 3 — upgrade via Homebrew (`brew install bash`) or use zsh |
| **PowerShell 5.1+** or **PowerShell 7+** | Only needed if you use the `.ps1` scripts instead of the bash version (Windows, or cross-platform `pwsh`) |
| **git** | Recommended for installation and updates |

## Clone (recommended)

```bash
git clone https://github.com/willhallonline/docker-devtools-aliases.git ~/.docker-devtools
```

Cloning lets you pull future updates with a simple `git pull`.

## Bash / zsh

Add the following line to your `~/.bashrc` or `~/.zshrc`:

```bash
source ~/.docker-devtools/docker-devtools.sh
```

Then reload your shell:

```bash
source ~/.bashrc   # or: source ~/.zshrc
```

## PowerShell

Clone to a location of your choice (e.g. `~/.docker-devtools` also works on Windows/PowerShell), then add the following line to your PowerShell profile (`$PROFILE`):

```powershell
. "$HOME/.docker-devtools/docker-devtools.ps1"
```

Reload your profile, or open a new session:

```powershell
. $PROFILE
```

The PowerShell scripts (`docker-devtools.ps1`, `js/docker-js-devtools.ps1`, `php/docker-php-devtools.ps1`, `images/docker-image-devtools.ps1`) mirror the bash versions tool-for-tool and work on Windows PowerShell 5.1+ and cross-platform PowerShell 7+ (`pwsh` on Linux/macOS). Bash `alias`es become PowerShell functions of the same name (e.g. `node-docker`, `phpcs-drupal`), since PowerShell aliases can't carry baked-in arguments.

## Optional add-on modules

The core `docker-devtools.sh` / `docker-devtools.ps1` script only sources the JS/CSS, PHP, and Python aliases automatically. Image tools and AI tools are opt-in — see [Available tools](tools) for how to enable them.

## Updating

```bash
cd ~/.docker-devtools
git pull
```

## Next steps

Head to [Available tools](tools) to see every alias, or jump straight to [Configuration](configuration) to tune TTY behaviour, file ownership, and extra Docker flags.

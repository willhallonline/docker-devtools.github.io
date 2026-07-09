---
title: Troubleshooting
layout: default
nav_order: 6
description: "Common Docker DevTools errors and how to fix them."
permalink: /troubleshooting
---

# Troubleshooting

**`docker-devtools: docker is not installed or not in PATH.`**
Docker is missing or the daemon is not running. Install Docker or ensure `docker` is on your `PATH`.

**Output files are owned by root**
Set `DOCKER_DEVTOOLS_MAP_HOST_USER=true` so the container runs as your UID/GID. See [Configuration](configuration).

**`the input device is not a TTY` in a script or CI**
Set `DOCKER_DEVTOOLS_TTY=never` (or `auto`) to suppress the `-it` flag.

**`invalid DOCKER_DEVTOOLS_TTY value`**
The variable must be exactly `always`, `auto`, or `never`.

**`invalid DOCKER_DEVTOOLS_MAP_HOST_USER value`**
The variable must be a recognised boolean: `true`/`false`, `1`/`0`, `yes`/`no`, or `on`/`off`.

---

Still stuck? [Open an issue](https://github.com/willhallonline/docker-devtools-aliases/issues) on the `docker-devtools-aliases` repository.

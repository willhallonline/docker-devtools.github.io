---
title: Testing
layout: default
nav_order: 5
description: "Running the bundled bash and PowerShell test harnesses for Docker DevTools."
permalink: /testing
---

# Testing

A shell-based test harness is included. It stubs out Docker and the alias sub-files so no containers are pulled.

```bash
bash tests/run_tests.sh
```

Requires bash 4+. All 42 assertions cover argument validation, TTY mode, host-user mapping, extra args, entrypoint overrides, and error handling.

A matching PowerShell test harness (`tests/run_tests.ps1`) covers the same scenarios for the `.ps1` scripts:

```powershell
pwsh tests/run_tests.ps1
```

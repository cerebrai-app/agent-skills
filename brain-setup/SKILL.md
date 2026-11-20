---
name: brain-setup
description: Initialize a second-brain vault with brainctl. Use when the user runs /brain-setup or asks to set up their second brain.
disable-model-invocation: true
---

# /brain-setup

1. **Check `brainctl` is installed.** Run `command -v brainctl` (PowerShell: `Get-Command brainctl`). If it is missing, stop and tell the user to install it:
   - macOS / Linux: `brew install --cask cerebrai-app/tap/brainctl`
   - Windows: `scoop bucket add cerebrai https://github.com/cerebrai-app/scoop-bucket`, then `scoop install cerebrai/brainctl`
2. **Run `brainctl init`** from the current directory. `brainctl` uses `BRAIN_HOME` itself when it is set, so do not `cd` or pass a path; check it first (`echo "$BRAIN_HOME"`, PowerShell: `$env:BRAIN_HOME`), and if it is empty the current directory becomes the vault, so confirm that directory with the user first. Pass `--python-version` (such as `3.14` or `3.14t`) only if the user asked for a Python version. It writes `.brain/config.yaml` (an existing one is kept and checked) and downloads Python, which needs network access.
3. **Report the result.** If it fails, show the error and stop. If `$BRAIN_HOME` was not set, `init` ends by printing the line that sets it for the user's shell and the profile to add it to: pass that on and do not edit their profile yourself.

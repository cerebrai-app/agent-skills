---
name: brain-setup
description: Initialize a second-brain vault with brainctl. Use when the user runs /brain-setup or asks to set up their second brain.
disable-model-invocation: true
---

# /brain-setup

1. **Check `brainctl` is installed.** Run `command -v brainctl` (PowerShell: `Get-Command brainctl`). If it is missing, stop and tell the user to install it:
   - macOS / Linux: `brew install --cask cerebrai-app/tap/brainctl`
   - Windows: `scoop install cerebrai/brainctl`
2. **Run `brainctl init`** in the vault: `$BRAIN_HOME` if set, otherwise the current directory. Pass `--python-version` or `--variant` only if the user asked for them. It writes `.brain/config.yaml` (an existing one is kept and checked) and downloads Python, which needs network access.
3. **Report the result.** If it fails, show the error and stop. If `$BRAIN_HOME` was not set, `init` ends by printing the line that sets it for the user's shell and the profile to add it to: pass that on and do not edit their profile yourself.

# agent-skills

Agent skills for the cerebrai Second Brain: a vault of notes, tasks, projects, areas and people
with a `.brain/` directory for its configuration.

## Skills

| Skill | What it does |
| --- | --- |
| [`brain-setup`](brain-setup/SKILL.md) | Checks that `brainctl` is installed and runs `brainctl init` to create the vault. Runs only when you invoke it. |

## Requirements

- [`brainctl`](https://github.com/cerebrai-app/go-cerebrai) on your `PATH`:
  `brew install --cask cerebrai-app/tap/brainctl` (macOS and Linux), or on Windows
  `scoop bucket add cerebrai https://github.com/cerebrai-app/scoop-bucket` then
  `scoop install cerebrai/brainctl`.

## Install

### Claude Code

```text
/plugin marketplace add cerebrai-app/agent-skills
/plugin install brain@cerebrai
```

On Claude Code 2.1.275 or later this works in one step:
`/plugin install brain --marketplace cerebrai-app/agent-skills`.

Plugin skills are namespaced by the plugin, so you invoke it as `/brain:brain-setup`.

### Other agents

With the [`skills`](https://www.npmjs.com/package/skills) CLI:

```sh
npx skills add cerebrai-app/agent-skills
```

Installed this way it is invoked as `/brain-setup`.

## Getting started

In the directory for your vault, run `/brain:brain-setup` (Claude Code) or `/brain-setup` (other
agents).

## Repository automation

The workflows in [`.github/workflows/`](.github/workflows) call the shared actions in
[cerebrai-app/actions](https://github.com/cerebrai-app/actions): `claude.yml` (answers `@claude`
mentions), `claude-code-review.yml` (reviews every PR), `release-notes.yml` (writes release notes
for each `vX.Y.Z` tag; its `about` input describes the repo) and `renovate.yml` (weekly Renovate,
configured by [`renovate.json`](renovate.json)). They need these secrets at the repository or
organization level:

- `CLAUDE_CODE_OAUTH_TOKEN` — for the Claude workflows, release notes included.
- `RENOVATE_APP_CLIENT_ID`, `RENOVATE_APP_PRIVATE_KEY` — for Renovate. Until they exist the job
  only prints a warning.

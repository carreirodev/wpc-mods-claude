# WPC Mods for Claude

**English** · [Português (Brasil)](README.pt-BR.md)

A Claude Code marketplace that gathers my mods in one place. Adding the marketplace installs nothing: you pick the mods you want, one by one.

## Mods

| Mod | Id | What it does |
| --- | --- | --- |
| [Status Pills](https://github.com/carreirodev/mod-status-pills) | `status-pills` | A band of pills by the prompt: model and effort, context, the 5-hour and 7-day limits with their resets, project and branch |
| [Agents Panel](https://github.com/carreirodev/mod-painel-agents) | `agents-panel` | A side pane with every agent of the session (model, effort, stopwatch and token usage) and its background shells |
| [Prompt Enhancer](https://github.com/carreirodev/mod-prompt-enhancer) | `prompt-enhancer` | Enhance and Send buttons above the prompt: rewrites the draft in place, clearer for the AI, without adding anything |
| [Plan Pill Progress](https://github.com/carreirodev/mod-plan-pill-progress) | `plan-progress` | Live plan progress bars above the prompt, with soft sounds |

Each mod lives in its own repository, whose README covers it in detail.

## Install

There are two ways, and they do the same thing: pick one.

**Inside Claude Code**, in a session:

1. Add the marketplace:

   ```
   /plugin marketplace add carreirodev/wpc-mods-claude
   ```

2. Install each mod you want by its id, for example:

   ```
   /plugin install status-pills@wpc-mods-claude
   ```

   Or open `/plugin`, go to the **Discover** tab and pick from there.

**From a terminal**, outside Claude Code:

1. Add the marketplace:

   ```
   claude plugin marketplace add carreirodev/wpc-mods-claude
   ```

2. Install each mod you want by its id, for example:

   ```
   claude plugin install status-pills@wpc-mods-claude
   ```

Either way, start a new session afterwards, or run `/reload-plugins` in one that's already open.

WSL has its own Claude Code install, separate from Windows: repeat the steps inside WSL too.

### If you already installed a mod from its own repository

Each mod also has its own marketplace, in its repository. Uninstall the old copy before installing from here: with the same mod installed from two marketplaces, both show as enabled, but only one runs.

To see where each mod came from, run this in a terminal, outside Claude Code:

```
claude plugin list
```

The name after the `@` is the marketplace. To remove an old copy, for example `status-pills@status-pills`:

```
claude plugin uninstall status-pills@status-pills
```

## Update

Updates aren't automatic. To fetch a mod's new version, run this in a terminal, outside Claude Code:

```
claude plugin update status-pills@wpc-mods-claude
```

Then start a new session, or run `/reload-plugins`.

So you don't have to remember: in `/plugin`, on the **Marketplaces** tab, pick `wpc-mods-claude` and then **Enable auto-update**.

## Add a mod to this marketplace

Add an entry to `plugins` in [`.claude-plugin/marketplace.json`](.claude-plugin/marketplace.json):

- Mod at the root of its repository: `"source": { "source": "github", "repo": "carreirodev/<repo>" }`
- Mod in a subfolder: `"source": { "source": "git-subdir", "url": "carreirodev/<repo>", "path": "<subfolder>" }`

The entry's `name` must match the `name` in the mod's `plugin.json`. Check it with `claude plugin validate .` and push to GitHub; anyone who already has the marketplace sees the new mod after `/plugin marketplace update wpc-mods-claude`.

Installed copies only get a mod's new code when the `version` in its `plugin.json` changes, so bump it on every release.

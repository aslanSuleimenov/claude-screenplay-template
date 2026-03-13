Sync reference files from the plugin into this project. Run after a plugin update, or when you want local editable copies of the genre compass files.

## What gets synced

1. **avoid-ai-writing-tells.md** — AI pattern checklist, from plugin to `analytics/`
2. **Compass genre files** — from `${CLAUDE_PLUGIN_ROOT}/compass/` to `compass/` in this project

## Step 1: Sync avoid-ai-writing-tells.md

Read `${CLAUDE_PLUGIN_ROOT}/analytics/avoid-ai-writing-tells.md`.
Write its content to `analytics/avoid-ai-writing-tells.md` in the current project.
Report: "✓ analytics/avoid-ai-writing-tells.md updated"

## Step 2: Sync compass files

Read each of the following files and write them to the corresponding path in the current project:

| Plugin source | Local destination |
|---|---|
| `${CLAUDE_PLUGIN_ROOT}/compass/INDEX.md` | `compass/INDEX.md` |
| `${CLAUDE_PLUGIN_ROOT}/compass/fiction/thriller.md` | `compass/fiction/thriller.md` |
| `${CLAUDE_PLUGIN_ROOT}/compass/fiction/black-comedy.md` | `compass/fiction/black-comedy.md` |
| `${CLAUDE_PLUGIN_ROOT}/compass/fiction/sci-drama.md` | `compass/fiction/sci-drama.md` |
| `${CLAUDE_PLUGIN_ROOT}/compass/fiction/coming-of-age.md` | `compass/fiction/coming-of-age.md` |
| `${CLAUDE_PLUGIN_ROOT}/compass/fiction/drama.md` | `compass/fiction/drama.md` |
| `${CLAUDE_PLUGIN_ROOT}/compass/doc/portrait.md` | `compass/doc/portrait.md` |
| `${CLAUDE_PLUGIN_ROOT}/compass/doc/verite.md` | `compass/doc/verite.md` |

Create directories `compass/fiction/` and `compass/doc/` if they don't exist.

Report each file: "✓ compass/fiction/thriller.md"

## Step 3: Summary

```
Sync complete.

Updated:
- analytics/avoid-ai-writing-tells.md
- compass/ (8 files)

Local compass files now take precedence — edit them freely for this project.
To reset to plugin defaults, run /sync-plugin-files again.
```

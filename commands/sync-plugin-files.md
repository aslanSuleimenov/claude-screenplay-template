Sync reference files from the plugin into this project. Run after a plugin update, or when you want local editable copies of the genre compass files.

## What gets synced

1. **avoid-ai-writing-tells.md** — AI pattern checklist, from plugin to `analytics/`
2. **All compass files** — from `${CLAUDE_PLUGIN_ROOT}/compass/` to `compass/` in this project

---

## Step 1: Sync avoid-ai-writing-tells.md

Read `${CLAUDE_PLUGIN_ROOT}/analytics/avoid-ai-writing-tells.md`.
Write its content to `analytics/avoid-ai-writing-tells.md` in the current project.
Report: "✓ analytics/avoid-ai-writing-tells.md"

---

## Step 2: Sync compass files

Read `${CLAUDE_PLUGIN_ROOT}/compass/INDEX.md` to get the full list of compass files.

For every file referenced in INDEX.md:
1. Read it from `${CLAUDE_PLUGIN_ROOT}/compass/[path]`
2. Write it to `compass/[path]` in the current project
3. Create subdirectories as needed
4. Report each file: "✓ compass/[path]"

Also sync the structural contract and reference files that may not be listed in INDEX.md:
- `${CLAUDE_PLUGIN_ROOT}/compass/fiction/genre-mechanics.md` → `compass/fiction/genre-mechanics.md`
- `${CLAUDE_PLUGIN_ROOT}/compass/doc/genre-mechanics.md` → `compass/doc/genre-mechanics.md`
- `${CLAUDE_PLUGIN_ROOT}/compass/doc/interview-structure.md` → `compass/doc/interview-structure.md`

---

## Step 3: Sync converter

Read all files from `${CLAUDE_PLUGIN_ROOT}/converter_MD_DOCX/` and write them to `converter_MD_DOCX/` in the current project.
Report each file: "✓ converter_MD_DOCX/[filename]"

---

## Step 4: Summary

```
Sync complete.

Updated:
- analytics/avoid-ai-writing-tells.md
- compass/ (N files)
- converter_MD_DOCX/ (N files)

To update again after a plugin upgrade, run /sync-plugin-files.
```

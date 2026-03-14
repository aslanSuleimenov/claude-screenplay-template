Initialize a new screenplay project in the current directory.

Argument: `$ARGUMENTS` — optional path to a draft or existing script file.

---

## Step 1: Extract data from file (if provided)

If `$ARGUMENTS` is not empty:
- Read the file at `$ARGUMENTS`
- Extract as much as possible:
  - **Type** — fiction if you see slug lines (INT./EXT.), scene headings, dialogue blocks; documentary if you see VIDEO/AUDIO tables or AV-script structure
  - **Title** — from the first heading or title block
  - **Genre** — infer from tone, setting, content
  - **Logline** — from any explicit logline, or summarize the premise in one sentence
  - **Format** — feature / short / series based on scope and length
  - **Theme** — what the story is about at a deeper level
  - **Setting** — locations and environment mentioned
  - **Period** — time period, season
  - **Runtime** — estimate from word count (~170 words = 1 min for fiction, ~340 words = 2 min for documentary AV)
  - **Characters** — names, rough roles, ages if mentioned
  - **Structural model** — infer from structure or default to three-act

If `$ARGUMENTS` is empty: all fields start as unknown.

---

## Step 2: Ask only about missing fields

For each field that could NOT be reliably determined, ask via AskUserQuestion — one question at a time.

Fields to fill:
1. **Type** — fiction or documentary?
2. **Title**
3. **Genre** (black comedy / thriller / drama / documentary portrait / cinema verité / other)
4. **Logline** — one sentence: who, what's at stake, what the conflict is
5. **Format** (feature / short / pilot / series)
6. **Theme** — deeper meaning
7. **Seed** — one image, metaphor, or contradiction the whole story grows from. Not a summary — a root. Example: "a man who builds walls to protect himself ends up trapped inside them." If the user can't articulate it yet — leave it blank, they'll fill it in later.
8. **Target audience**
9. **Setting**
10. **Period**
11. **Currency and locale** (names, place names, character language)
12. **Runtime** in minutes
13. **Structural model** (three-act / five-loop / other) — ask only if the user mentioned a specific structure or if the draft has an unusual shape. Otherwise default to three-act and don't ask.

If a field was extracted from the file with confidence — use it, do not ask. If uncertain — ask.

Before asking, show what you found:
> "Found in the file: Type = fiction, Title = «...», Genre = thriller. Still need: logline, audience, runtime."

---

## Step 3: Create project structure

Create directories if they don't exist: `scenes/`, `analytics/`, `versions/`

---

## Step 4: Write CLAUDE.md

Write `CLAUDE.md` with all actual values:

```
# CLAUDE.md

## Project

- **Type:** [fiction or documentary]
- **Title:** [title]
- **Genre:** [genre]
- **Logline:** [logline]
- **Format:** [format]
- **Theme:** [theme]
- **Seed:** [one image or metaphor the story grows from — or blank]
- **Target audience:** [audience]
- **Setting:** [setting]
- **Period:** [period]
- **Currency and locale:** [locale]
- **Runtime:** [N min]
- **Story structure:** [model]

Working language: **English**. All responses and comments in English.

## Characters

| Name | Age | Role | External goal | Inner need |
|------|-----|------|---------------|------------|
[rows for each character found — or empty if none]

<!-- External goal: what the character is actively pursuing (visible, concrete)  -->
<!-- Inner need: what they must change or accept in themselves — often the opposite of what they want -->

## Structure

### Scenes

| # | File | Act/Loop | Key event | Status |
|---|------|----------|-----------|--------|

### Structural beats

---

## Scene formatting

[Insert the correct block based on type — see below]

## Working rules

- Do NOT renumber files without an explicit command
- When adding a scene — update the scenes table above and "Change log"
- Inserting scenes between existing ones → renumber subsequent scenes (whole numbers only, no letter suffixes)
- File renaming: two-phase rename via temp names (avoid collisions on Windows)
- AI writing patterns are forbidden — see `analytics/avoid-ai-writing-tells.md`
- Write only what the camera sees: actions, not emotions. Not "Mary is sad" — but "Mary stares out the window, cigarette burned down untouched." Strong verbs, specific details.

## Callbacks / Running gags

| Element | From → To |
|---------|-----------|

## Protected zones (no humor)

## Change log

| Date | Change |
|------|--------|
| [today] | Project initialized via /startproject |
```

**Scene formatting block — fiction:**

```
## Scene formatting

Strictly per screenplay format. Quick rules:

# Scene 01: Title

**INT./EXT. LOCATION — TIME OF DAY**

Action description. Present tense, third person. Max 4 lines per paragraph.

**CHARACTER NAME**
*(parenthetical)*
Dialogue text.

- ONE blank line between blocks; ZERO between name and dialogue
- Names — **bold caps**: `**NAME**`
- Slug line — **bold**: `**INT. LOCATION — DAY**`
- First appearance: `NAME (age)` in caps within action text
- Do not use: `FADE OUT.`, `CUT TO:`, `CLOSE ON:`
- Numbers in dialogue — written out as words
- `---` — location change within a scene (converter skips it)
- `> **PALETTE:** ...` — visual note
```

**Scene formatting block — documentary:**

```
## Scene formatting

Strictly two-column AV format. Quick rules:

# Block 01: Title

| VIDEO | AUDIO |
|-------|-------|
| WS. Mountains, dawn. | *(NAT SOUND: wind)* |
| MS. Shepherd leads the flock. | **V/O:** Voice-over text. |
| CU. Subject's face. | **SOT AIBEK:** "Direct quote." |
| **SUPER:** Aibek, shepherd, 43 | |
| B-ROLL: yurts, smoke, kettle. | *(MUSIC: komuz, low)* |

- Each block = one file `scenes/NN_name.md`
- Table `| VIDEO | AUDIO |` — mandatory
- Labels: **V/O**, **SOT**, **SUPER**, **NAT SOUND**, **SFX**, **B-ROLL**
- Shot sizes: WS, MS, CU, ECU, AERIAL
- `> **NOTE:** ...` — director's note (not in DOCX)
```

---

## Step 5: Write scenes/00_title.md

```
# [TITLE]

**[GENRE]**
*[project type]*

[Logline]

Author: —
[Year]
```

---

## Step 6: Copy avoid-ai-writing-tells from plugin

Read `${CLAUDE_PLUGIN_ROOT}/analytics/avoid-ai-writing-tells.md` and write to `analytics/avoid-ai-writing-tells.md`.

**Compass files are NOT copied here.** Agents and commands read them directly from the plugin via `${CLAUDE_PLUGIN_ROOT}/compass/`. To get local editable copies, the user runs `/sync-plugin-files`.

---

## Step 7: Create memory/ and write START_HERE.md

Create directory `memory/` if it doesn't exist.

Write `START_HERE.md` to the project root. Content — read from `${CLAUDE_PLUGIN_ROOT}/START_HERE.md` and write as-is.

---

## Step 8: Confirm

Tell the user:

```
Project "[Title]" initialized.

Created:
- CLAUDE.md
- scenes/00_title.md
- analytics/avoid-ai-writing-tells.md
- memory/
- START_HERE.md

Genre compass: read from plugin (${CLAUDE_PLUGIN_ROOT}/compass/).
To get local editable copies: /sync-plugin-files

Next steps:
- /split [path to draft] — break a draft into scenes
- /new-scene 01 Title — write the first scene from scratch
- /compass [genre — logline] — genre analysis and reference films
```

If the file argument was provided, also say:
> "Source file read: `[filename]`. [N] characters extracted. Run /split [filename] to break it into scenes."

# CLAUDE.md

<!-- Filled in by /startproject. Do not edit manually. -->

## Project

- **Type:** —
- **Title:** —
- **Genre:** —
- **Logline:** —
- **Format:** —
- **Theme:** —
- **Seed:** —
- **Target audience:** —
- **Setting:** —
- **Period:** —
- **Currency and locale:** —
- **Runtime:** —
- **Story structure:** —

Working language: **English**. All responses and comments in English.

## Characters

<!-- Filled in by /startproject -->

| Name | Age | Role | External goal | Inner need |
|------|-----|------|---------------|------------|

## Structure

<!-- Filled in by /startproject -->

### Scenes

| # | File | Act/Loop | Key event | Status |
|---|------|----------|-----------|--------|

### Structural beats

<!-- Filled in by /startproject -->

---

## Scene formatting

<!-- /startproject replaces this block with the correct format based on project type -->

### If type = fiction

Strictly per `converter_MD_DOCX/README.md`. Quick rules:

```markdown
# Scene 01: Title

INT./EXT. LOCATION — TIME OF DAY

Action description. Present tense, third person. Max 4 lines per paragraph.

CHARACTER NAME
*(parenthetical)*
Dialogue text.
```

- Exactly ONE blank line between blocks (action → name, dialogue → next action); NEVER two blank lines before a character name; ZERO blank lines between name and dialogue
- Names — CAPS, plain text (no asterisks)
- Slug line — plain text: `INT. LOCATION — DAY`
- First appearance: `NAME (age)` in caps within action text
- Do not use: `FADE OUT.`, `CUT TO:`, `CLOSE ON:`
- Numbers in dialogue — written out as words
- `---` — location change within a scene (converter skips it)
- `> **PALETTE:** ...` — visual note

### If type = documentary

Strictly per `converter_MD_DOCX/README.md`, section "Documentary format". Quick rules:

```markdown
# Block 01: Title

| VIDEO | AUDIO |
|-------|-------|
| WS. Mountains, dawn. | *(NAT SOUND: wind)* |
| MS. Shepherd leads the flock. | **V/O:** Voice-over text. |
| CU. Subject's face. | **SOT AIBEK:** "Direct quote." |
| **SUPER:** Aibek, shepherd, 43 | |
| B-ROLL: yurts, smoke, kettle. | *(MUSIC: komuz, low)* |
```

- Each block = one file `scenes/NN_name.md`
- Table `| VIDEO | AUDIO |` — mandatory format
- Labels: **V/O** (voice-over), **SOT** (sync/interview), **SUPER** (title card), **NAT SOUND**, **SFX**, **B-ROLL**
- Shot sizes: WS, MS, CU, ECU, AERIAL
- `> **NOTE:** ...` — director's note (not included in DOCX)

## Working rules

- Do NOT renumber files without an explicit command
- When adding a scene — update the table above and "Change log"
- Expanding by inserting scenes between existing ones → renumber subsequent scenes (whole numbers only, no letter suffixes)
- File renaming: two-phase rename via temp names (avoid collisions)
- AI writing patterns are forbidden — see `analytics/avoid-ai-writing-tells.md`
- Write only what the camera sees: actions, not emotions. Not "Mary is sad" — but "Mary stares out the window, cigarette burned down untouched." Strong verbs, specific details.

## Callbacks / Running gags

<!-- Filled in as work progresses -->

| Element | From → To |
|---------|-----------|

## Protected zones (no humor)

<!-- Filled in by author -->

## Change log

| Date | Change |
|------|--------|

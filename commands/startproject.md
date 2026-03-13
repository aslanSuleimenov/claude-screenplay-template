Initialize a new screenplay project in the current directory. Ask questions one at a time using AskUserQuestion, wait for each answer before proceeding.

## Questions

1. Project type: **fiction** or **documentary**?
2. Project title?
3. Genre (black comedy / thriller / drama / documentary portrait / cinema verité / other)?
4. Logline — one sentence: who, what's at stake, what the conflict is?
5. Format (feature / short / pilot / series)?
6. Theme — what is it about at a deeper level?
7. Target audience?
8. Setting (country, city, environment)?
9. Season and time period?
10. Currency and cultural specifics (names, place names, language of characters)?
11. Target runtime in minutes?
12. Structural model (three-act / five-loop / other)?

## After all answers — create the project structure

### 1. Create directories

Create if they don't exist:
- `scenes/`
- `analytics/`
- `versions/`

### 2. Write CLAUDE.md

Write `CLAUDE.md` with the actual values from the answers (not dashes):

```
# CLAUDE.md

## Project

- **Type:** [fiction or documentary]
- **Title:** [title]
- **Genre:** [genre]
- **Logline:** [logline]
- **Format:** [format]
- **Theme:** [theme]
- **Target audience:** [audience]
- **Setting:** [setting]
- **Period:** [period]
- **Currency and locale:** [locale]
- **Runtime:** [N min]
- **Story structure:** [model]

Working language: **English**. All responses and comments in English.

## Characters

| Name | Age | Role | Want / Need |
|------|-----|------|-------------|

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

```markdown
# Scene 01: Title

**INT./EXT. LOCATION — TIME OF DAY**

Action description. Present tense, third person. Max 4 lines per paragraph.

**CHARACTER NAME**
*(parenthetical)*
Dialogue text.
` `` `

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

```markdown
# Block 01: Title

| VIDEO | AUDIO |
|-------|-------|
| WS. Mountains, dawn. | *(NAT SOUND: wind)* |
| MS. Shepherd leads the flock. | **V/O:** Voice-over text. |
| CU. Subject's face. | **SOT AIBEK:** "Direct quote." |
| **SUPER:** Aibek, shepherd, 43 | |
| B-ROLL: yurts, smoke, kettle. | *(MUSIC: komuz, low)* |
` `` `

- Each block = one file `scenes/NN_name.md`
- Table `| VIDEO | AUDIO |` — mandatory
- Labels: **V/O**, **SOT**, **SUPER**, **NAT SOUND**, **SFX**, **B-ROLL**
- Shot sizes: WS, MS, CU, ECU, AERIAL
- `> **NOTE:** ...` — director's note (not in DOCX)
```

### 3. Write scenes/00_title.md

```
# [TITLE]

**[GENRE]**
*[project type]*

[Logline]

Author: —
[Year]
```

### 4. Write analytics/avoid-ai-writing-tells.md

Write the following content verbatim:

```
# AI Writing Tells — What to Avoid

## Structural patterns

1. **Rule of three adjectives** — exactly 3 adjectives/epithets in a row. Replace with one precise word.
2. **Significance tail** — ending a sentence with "...and that changed everything", "...and life would never be the same." Cut.
3. **Emotional placeholder stage directions** — "looks thoughtfully", "sighs meaningfully", "smiles sadly". Replace with a physical action.
4. **Dialogue that explains feelings** — "I feel like you're pulling away from me." Replace with subtext or silence.
5. **Parallel construction overload** — three sentences in a row with identical structure. Break the rhythm.
6. **Thematic declaration in dialogue** — a character explains the theme directly. Never. Show it through action.
7. **False modesty opener** — "It's worth noting that...", "It's important to understand...", "One might argue..." Delete.
8. **Hedge stack** — "perhaps", "possibly", "in some ways", "to a certain extent" — in one sentence. Pick one or cut all.
9. **Echoed keyword** — the same word appears 3+ times in a paragraph. Vary.
10. **Resolution ribbon** — the last paragraph ties everything up neatly and optimistically. Resist.

## Russian-language markers (for Russian-language projects)

11. **Канцелярит-связки** — «в рамках», «на сегодняшний день», «в контексте», «осуществляет деятельность».
12. **Псевдоглубокие абстракции** — «истинная суть», «глубинный смысл», «подлинное предназначение».
13. **Перечисление через «а также»** — «...а также другие важные аспекты».
14. **Официозный пассив** — «было принято решение», «является неотъемлемой частью».
15. **Нарративный костыль** — «следует отметить, что», «необходимо подчеркнуть».
16. **Тавтологичное усиление** — «полностью и окончательно», «абсолютно точно», «совершенно очевидно».
17. **Тройной синоним** — «думает, размышляет и анализирует» — три слова там, где хватит одного.
18. **Ложная многозначительность** — короткий абзац, который звучит глубоко, но ничего не говорит.
19. **Эмоциональный итог в конце сцены** — «Это был важный момент для обоих». Показывай, не объясняй.
```

### 5. Confirm

Tell the user:

```
Project "[Title]" initialized.

Created:
- CLAUDE.md
- scenes/00_title.md
- analytics/avoid-ai-writing-tells.md
- scenes/, analytics/, versions/ directories

Next steps:
- /split [path to draft] — if you have a draft to break into scenes
- /new-scene 01 Title — to write the first scene from scratch
- /compass [genre — logline] — for genre analysis and reference films
```

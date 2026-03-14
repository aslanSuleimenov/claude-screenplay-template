Read a screenplay draft and split it into scenes/blocks. Argument: $ARGUMENTS (file path).

## Step 1 — Determine project type

Read CLAUDE.md — the **Type** field (fiction or documentary).

## Step 2 — Read the file

Read the file at the given path in full. This is a draft — flat text, no strict formatting.

**Large files (>50 pages / >15000 words):** if the file is very large, process in parts — first third, then second, then third. Create scene files as each part is processed.

## Step 3 — Identify boundaries

### Fiction
Look for scene-change markers:
- Slug lines: INT. / EXT. — start of a new scene
- Headings like "SCENE", "Scene", scene numbers
- Location change with explicit place name
- If no markers — divide by meaningful blocks (change of place, time, participants)

### Documentary
Look for block-change markers:
- Change of topic, subject, shooting location
- Transition from interview to narration or vice versa
- Explicit text dividers (***, ---, headings)
- If no markers — divide by thematic blocks

## Step 4 — Create files

For each unit create a file `scenes/NN_title.md` (two-digit numbering; if >99 units — three digits).

### Fiction format
Strictly per converter_MD_DOCX/README.md:
```markdown
# Scene NN: Scene title

INT./EXT. LOCATION — TIME OF DAY

Action description.

CHARACTER NAME
*(parenthetical if any)*
Dialogue text.
```

### Documentary format
Strictly per converter_MD_DOCX/README.md:
```markdown
# Block NN: Block title

| VIDEO | AUDIO |
|-------|-------|
| WS. Shot description. | **V/O:** Voice-over text. |
| CU. Subject's face. | **SOT ИМЯ:** "Direct speech." |
| B-ROLL: details. | *(NAT SOUND: description)* |
```

## Step 5 — Extract characters/subjects

### Fiction
Find all character names (lines in CAPS before dialogue).

### Documentary
Find all subjects (names after SOT, mentions in V/O, names in SUPER).

## Step 6 — Fill in CLAUDE.md

Update:
- **Characters table** — name, age/role, function
- **Scenes table** — number, file, key event/topic
- **Structural beats** — key structural moments

Add an entry to "Change log".

## Step 7 — Summary

Output:
- How many scenes/blocks were created
- List of files
- Characters/subjects found
- What needs manual review

Tell the user: "Next step: /compass [genre] — [logline]"

---
name: draft-polish
description: Processes a screenplay draft through iterative passes — from analysis to final cleanup. Run when you have raw text and need to turn it into finished scenes. Argument: path to draft file.
---

You process a screenplay draft through multiple passes. Before each pass you explain to the user what you're about to do and ask for permission. Before writing any file — you ask first.

Argument at invocation: `$ARGUMENTS` — path to the draft file relative to the project root.

---

## Setup

Read CLAUDE.md — get the project type (fiction / documentary / vertical microdrama), title, genre, logline, runtime.

Read the draft file at `$ARGUMENTS`.

Create a backup: copy the draft to `versions/backup_draft_YYYYMMDD.md` (today's date). Tell the user: "Backup saved to versions/."

---

## Pass 0 — Draft Analysis

Extract from the text:
- **Title** — is it in the text? If not — suggest options and ask
- **Type** (fiction / documentary / vertical microdrama) — take from CLAUDE.md; if empty — determine from the text, ask for confirmation
- **Genre** — determine from content; if multiple options — show them, ask
- **Runtime** — is it in CLAUDE.md? If not — ask; benchmark: 170 words ≈ 1 min (fiction), 340 words ≈ 2 min (vertical)
- **Scene count** — how many logical episodes are in the draft; how many are needed for the stated runtime

For each unclear field — ask a separate question via AskUserQuestion, not all at once.

After confirming all fields, output the summary card:

```
Title: ...
Type: ...
Genre: ...
Runtime: ... min
Scenes in draft: N
Scenes needed: ~N (by runtime)
```

Ask: "Continue to scene breakdown?"

---

## Pass 1 — Structure and Breakdown

Explain to the user before starting:
> "I'll break the draft into scenes. For each — title, runtime, one line about what happens. If there isn't enough material for the stated length — I'll show where you need to add and offer options."

Ask: "Shall we start?"

After confirmation — propose the scene plan as a table:

```
| # | Title | Min | What happens |
|---|-------|-----|--------------|
| 01 | ... | 2 min | ... |
```

If runtime doesn't add up — flag it clearly:
> "The draft runs 18 minutes, target is 40. Scenes 4, 7, 9 are missing — I'll offer options in the next pass."

Ask: "Does this plan work, or do you want changes?"

Wait for the response. Adjust the plan based on user feedback. Show the revised plan again and ask for confirmation.

---

## Pass 2 — Writing Scenes

Explain before starting:
> "Now I'll write each scene to scenes/. Where material is missing — I'll offer 2–3 options. For each scene I'll show what I plan to write and ask 'ok' before saving."

Ask: "Shall we start?"

For each scene:

1. Show the draft text of the scene (or offer options if there's no text)
2. If offering options — show 2–3 with a brief description of each
3. Ask via AskUserQuestion: "Write this scene to scenes/NN_title.md?"
4. After confirmation — write the file in the project format:
   - Fiction: heading `# Scene NN: Title`, slug line `**INT./EXT. LOCATION — DAY/NIGHT**`, names `**IN CAPS**`
   - Documentary: heading `# Block NN: Title`, table `| VIDEO | AUDIO |`
   - Vertical: heading `# Episode NN: Title`, ~340 words, cliffhanger at the end
5. Update the scene table in CLAUDE.md (add a row)

After writing all scenes — say: "N scenes written. Moving to review passes."

---

## Pass 3 — Logic and Genre

Explain before starting:
> "I'll check logic, chronology, characters, and genre alignment. I'll show a list of issues — you decide what to fix."

Ask: "Shall we start?"

After confirmation:

Read all created scenes/*.md.

Read analytics/compass_artifact.md if it exists. If not — find the genre file.

**Lookup rule:** for each path below, check the local project first (`compass/[path]`). If the file exists there — read it. If not — read from `${CLAUDE_PLUGIN_ROOT}/compass/[path]`.

- crime thriller → `fiction/thriller.md`
- black comedy → `fiction/black-comedy.md`
- sci-fi drama → `fiction/sci-drama.md`
- coming-of-age → `fiction/coming-of-age.md`
- drama → `fiction/drama.md`
- documentary portrait → `doc/portrait.md`
- cinema verité → `doc/verite.md`

If the exact genre isn't listed, check `compass/INDEX.md` (local or plugin) for the closest match.

Check:
- **Chronology**: events follow a logical order, no time contradictions
- **Characters**: a character behaves consistently across scenes, no unmotivated reversals
- **Props and details**: if there's a knife in scene 3, it can't vanish without explanation
- **Genre norms**: no violations from the compass file
- **Empty scenes**: no scenes without conflict or event

Output a list of issues by scene:
```
Scene 02: character Марта knows about the secret, but in scene 01 she didn't yet → needs explanation
Scene 05: no cliffhanger (genre requirement)
```

For each issue — suggest a fix and ask via AskUserQuestion: "Fix this?"

---

## Pass 4 — Spelling and Syntax

Explain before starting:
> "I'll go through all scenes: spelling, punctuation, syntax. I'll show a list of errors with corrections, then write everything at once or scene by scene — your call."

Ask: "Shall we start?"

After confirmation — go through all scenes/*.md. Output the error list:

```
scenes/02_meeting.md, line 14: error → correction
scenes/03_escape.md, line 7: extra comma
```

Ask: "Fix everything at once or show each change individually?"

Write the corrected files after confirmation.

---

## Pass 5 — AI Patterns

Explain before starting:
> "I'll check the text for signs of AI writing using analytics/avoid-ai-writing-tells.md. I'll show specific phrases and suggest replacements."

Ask: "Shall we start?"

Read analytics/avoid-ai-writing-tells.md.

Check all scenes. Key markers:
- Rule of three: exactly 3 adjectives in a row
- Emotional placeholders: "looks thoughtfully", "sighs", "meaningfully"
- Dialogue that explains feelings: "I feel that...", "It seems to me that..."
- Tail clichés: "and life would never be the same", "it changed everything"

Output the list with replacements:
```
scenes/01_start.md: "looks thoughtfully" → delete or replace with a physical action
scenes/04_conversation.md: "I feel like you're leaving" → "You're leaving." (pause)
```

Ask via AskUserQuestion: "Apply all replacements?"

---

## Final Report

After all passes, output:

```
Draft processed.

Scenes written: N
Files: scenes/01_... — scenes/NN_...
Backup: versions/backup_draft_YYYYMMDD.md

Pass 1 (structure): plan of N scenes
Pass 2 (writing): N files created
Pass 3 (logic): N issues found, N fixed
Pass 4 (spelling): N corrections
Pass 5 (AI patterns): N replacements

Next step: /compile to build the DOCX, or /analyze NN for a detailed scene review.
```

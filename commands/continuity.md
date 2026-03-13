Check the screenplay for continuity errors. Argument: $ARGUMENTS (optional — scene range, e.g. "10-20").

1. Read CLAUDE.md — characters, structure, setting, time
2. Read all scenes from scenes/ (or the specified range)
3. Check by category:

### Time
- Day/night sequence: does time jump backwards without explanation?
- Season: do details (clothing, weather, light) match the stated time of year?
- Duration: do the events fit within the stated period?

### Geography
- Character is in one city in scene 5, another in scene 6. Is there a travel scene?
- Distances: is it realistic to get there in the stated time?

### Appearance and props
- Clothing: does it change without reason?
- Objects: does something appear that wasn't established? Does something disappear?
- Injuries: if a character is hurt — are there consequences in following scenes?
- Object transfers: if an object passed from one character to another, who has it in the next scene?

### Character knowledge
- Does a character know something they haven't been told yet?
- Have they forgotten something they already learned?
- Is there a reaction to key events?

### Names and spelling
- Consistency of name spelling across scenes
- Do character names in the CLAUDE.md table match how they appear in the scenes?

### Callbacks
- Are all callbacks established in CLAUDE.md paid off?
- Any unresolved threads (character appears and disappears)?

### Seed / core image
- If CLAUDE.md has a Seed field — does that image or metaphor appear in the screenplay? Where?
- Does it echo across the structure, or only once?
- If absent — note as a gap, not an error

4. Output the report:

```
## Continuity Report

### Critical problems
(things that break logic)

### Warnings
(minor inconsistencies)

### Unresolved threads
(characters or objects without resolution)

### All clear
(what was checked and raises no questions)
```

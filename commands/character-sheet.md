Build a character sheet. Argument: $ARGUMENTS (character name).

1. Read CLAUDE.md — find the character in the table
2. Read ALL files from scenes/ in order
3. Find every mention of the character: dialogue, action lines, parentheticals
4. Build the sheet:

```
## CHARACTER NAME (age)

### Role
Who they are in the story: protagonist / antagonist / ally / ...

### First appearance
Scene NN — how introduced, what they do

### Scenes with this character
| Scene | What they do | Who they interact with |
|-------|-------------|----------------------|

### Voice portrait
- Typical phrases
- Speech manner (long/short lines, slang, pauses)
- How they address others

### Voice distinctiveness
Compare this character's speech to others: can you tell their lines apart without the name? What makes their voice unique? If their speech is indistinguishable from another character — flag it as a problem.

### Relationships
| Character | Type of relationship | Dynamic (growing/falling/stable) |
|-----------|---------------------|----------------------------------|

### Wants / Needs / Says

| Layer | What it is | From the text |
|-------|-----------|---------------|
| **Says** | What the character claims they want — stated explicitly in dialogue | |
| **Wants** | What they are actually pursuing through their actions | |
| **Needs** | What they must change or accept to resolve their inner conflict — often the opposite of what they want | |

If Says = Wants = Needs — the character has no subtext. Flag it.

### Arc
Where the character starts → what the pressure reveals → where they end up (or refuse to go)

### Appearance / props
All mentions of clothing, objects, physical details (with scene references)

### Problems
Contradictions, gaps, scenes where the character appears but doesn't serve the story
```

5. Output the sheet. Do not save to file — display only.

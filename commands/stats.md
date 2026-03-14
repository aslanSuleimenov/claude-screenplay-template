Show a full overview of the screenplay status.

## Part 1 — Scenes table

1. Read CLAUDE.md — determine project type
2. Read all files from scenes/ alphabetically
3. From each file extract the heading and count words
4. Output the table:

| # | File | Title | Words | Status |
|---|------|-------|------:|--------|

## Part 2 — Structure

5. Read CLAUDE.md — structural beats, acts/loops
6. Cross-check with the actual files: are all beats present, any gaps in numbering?
7. Output:
   - Which structural beats are written, which are not
   - Current runtime (fiction: ~170 words = 1 min; documentary AV: ~340 words = 2 min)
   - Deviation from target runtime

## Part 3 — Detailed statistics

### For fiction type
8. Count dialogue/action ratio (words in dialogue vs words in action lines)
9. Count scenes per character (how many scenes each character appears in)

### For documentary type
8. Count separately:
   - V/O words (voice-over text)
   - Number of SOT blocks (sync sound / interviews)
   - Number of SUPER title cards
9. Count blocks per subject

## Part 4 — Recommendation

10. What to write next: missing scenes, short scenes to expand, unresolved threads

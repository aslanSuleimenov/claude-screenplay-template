Create a new scene/block. Argument: $ARGUMENTS — number and title, e.g. `05 Bar` or `05: Mountains`.

1. Read CLAUDE.md — determine the **project type** (fiction or documentary), characters, structure, style.
   If the "Type" field is empty or not set — stop: "Project type not set. Run /startproject to configure the project."
2. Check for analytics/compass_artifact.md:
   - If it exists — read it (genre systems will help write the scene in the genre's style)
   - If not — continue without it, but recommend: "Run /compass to create the genre reference"
3. Read the genre entry matching the project's genre:
   - Fiction: `${CLAUDE_PLUGIN_ROOT}/compass/fiction/genre-mechanics.md`
   - Documentary: `${CLAUDE_PLUGIN_ROOT}/compass/doc/genre-mechanics.md`
   Find the section for this genre. Note: **Must happen** and **Forbidden**. Ask: does this scene/block serve one of the structural obligations, or does it violate a forbidden pattern?
3. Parse the argument: first number is the scene number, the rest is the title
4. If the number is taken or being inserted between existing ones — warn and ask for confirmation before renumbering. Do the renumbering two-phase (first temp names, then final names)

## If type = fiction

5. Write the scene strictly following converter_MD_DOCX/README.md (section "Screenplay Format"):
   - `# Scene NN: Title`
   - `**INT./EXT. LOCATION — TIME OF DAY**`
   - Character names in **BOLD CAPS**
   - One blank line between blocks, zero between name and dialogue

## If type = documentary

5. Write the block strictly following converter_MD_DOCX/README.md (section "Documentary Format"):
   - `# Block NN: Title`
   - Table `| VIDEO | AUDIO |`
   - **V/O:** for voice-over text, **SOT NAME:** for interviews
   - *(NAT SOUND: ...)*, *(MUSIC: ...)*, *(SFX: ...)* in italics
   - **SUPER:** for title cards, B-ROLL: for cutaways
   - Shot sizes: WS, MS, CU, ECU, AERIAL

## Common to both types

6. **Attractor check:** Every 7–10 minutes of screen time the audience needs an emotional impact — not necessarily action, but something that shifts their state: revelation, humor, shock, sudden intimacy, reversal. Estimate where this scene falls in the overall runtime. Is there an attractor nearby? If this scene is in a zone without one — either this scene carries it, or flag the gap.

7. Check against `${CLAUDE_PLUGIN_ROOT}/analytics/avoid-ai-writing-tells.md` — any forbidden patterns?
8. Save as `scenes/NN_title.md`
9. Update the scenes table and change log in CLAUDE.md

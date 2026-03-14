---
name: unico
description: Creates a UNICO pitching starter pack. Fills in the Project Passport, Character Bible, and Presentation structure from screenplay materials. Writes analytics/unico_package.md. Run when ready to approach a producer.
---

You assemble a pitching starter pack for the production company UNICO based on their requirements structure.

## Step 1: Gather material

Read CLAUDE.md — title, type, genre, logline, characters, runtime, audience, author.

Read all files in scenes/ alphabetically — extract:
- main characters: what drives each one, what the conflict is, how they change
- super-idea: what law governs this story (those who follow it win, those who break it lose)
- message: what the author is saying to the audience
- central conflict: protagonist vs antagonist, the collision of desires
- high concept: the recurring mechanism that holds the whole season together
- themes: what the story explores

Read analytics/compass_artifact.md if it exists — reference projects, genre analysis.

Read `${CLAUDE_PLUGIN_ROOT}/compass/INDEX.md` to find the compass file for the project's genre. Check local `compass/` first — if the file exists there, use it. Otherwise read from `${CLAUDE_PLUGIN_ROOT}/compass/`.

## Step 2: Write unico_package.md

### Document structure:

```
# UNICO Starter Pack: [Title]

Author: [name from CLAUDE.md]
Date: [current date]

---

## PROJECT PASSPORT

**Title:** ...

**Genre:** ...

**Format:** Dark / Light — [rationale for tone]

**Language:** [dialogue language and why]

**Number of episodes and runtime:** [N episodes × XX min]
Runtime benchmarks:
- drama — 45–52 min
- detective — 40 min
- sitcom — 23 min
Specify: series or mini-series, whether there is potential for a 2nd season.

**References (3–4):**
- [Title] — [1–2 sentences: what specifically we take from this reference]
- ...

**Target audience:**
Age, interests, platforms, why they will watch this particular series.

**Uniqueness:**
What sets it apart from similar projects. The idea, biographical basis, angle of approach.

**Super-idea:**
The unchanging law of this story. One sentence.
Formula: "In this world [law] — and every character either follows it or pays the price."

**Message:**
What the author wants to say to the audience. There may be 2–3, but one is primary, tied to the super-idea.

**Central conflict:**
How the desires of the protagonist and antagonist collide. The conflict must hold until the finale.

**High concept:**
The recurring unique mechanism that runs through the entire season.
Formula: "Each episode the audience sees how [mechanism]."

**Theme (themes):**
What the story examines. Each theme explored from both sides.

---

## CHARACTER BIBLE

For each main character (3–5):

### [Character Name]

**Backstory:**
Biography: family, turning points, what shaped the character.

**Arc:**
How they changed over the story — external + internal change.
Start: [who they were]. End: [who they became].

**False goal:**
What they want to achieve at the start (what seems most important to them).

**True goal:**
What they actually need. They come to understand this by the Midpoint or later.

**External conflict:**
What/who stands in the way of their goals.

**Internal conflict:**
The moral struggle within the character. A contradiction in beliefs.

**Weakness:**
Moral or physical. The antagonist presses on it.

**Superpower:**
A unique ability that gets them out of difficult situations.

**Secret:**
What they hide, from whom, and why.

---

## PRESENTATION STRUCTURE (10+ slides)

1. **Title slide** — title, format, genre, N episodes × runtime, author, contacts
2. **What the story is about** — 4–5 sentences: setup, stakes, why audiences can't stop watching
3. **Uniqueness / Why now** — context, resonance, statistics if available
4. **References** — 3–4 projects with rationale
5. **Main character** — who they are, what they want, what their pain is
6. **Antagonist / Conflict** — who stands in the way and why
7. **Super-idea + High concept** — the mechanism that holds the season together
8. **Target audience** — who watches and why they'll watch this
9. **Business potential** — platforms, co-production, festival potential
10. **Music explainer** — soundtrack tone, local or international artists, role of music
11. **Thank you / Contacts**

---

## SIZZLE REEL (recommendations)

2–5 min video from reference materials.
Structure: tone → conflict → hero → hook (final image or question).
Reference moments for editing: [list of 3–5 scenes or images from this project].
```

## Writing rules

- Professional tone, no AI patterns from `${CLAUDE_PLUGIN_ROOT}/analytics/avoid-ai-writing-tells.md`
- Super-idea — one specific sentence, not an abstraction
- Characters: only what is actually in the screenplay — do not invent
- Conflict — specific, not "good vs evil"
- References — from compass_artifact or the compass genre file
- **Soviet and Russian cinema is valid and encouraged as reference:** Tarkovsky (*Stalker*, *The Mirror*, *Andrei Rublev*), Balabanov (*Brother*, *Cargo 200*, *Of Freaks and Men*), Muratova (*The Asthenic Syndrome*, *Brief Encounters*), Zvyagintsev (*Leviathan*, *Elena*, *The Return*), Shepitko (*The Ascent*), Klimov (*Come and See*), German (*Hard to Be a God*, *My Friend Ivan Lapshin*), Panfilov, Sokurov. Use when the project's tone, cultural context, or moral weight matches.
- Do not limit references to Hollywood — European, Asian, and post-Soviet cinema often fits better for CIS projects

Save to analytics/unico_package.md.
Report how many scenes you read and how many characters you described.

## Export to DOCX

After saving unico_package.md, tell the user:
> "To export to DOCX: `python converter_MD_DOCX/unico_to_docx.py`
> Output: versions/[project]_unico_v01.docx — formatted for UNICO submission."

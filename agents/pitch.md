---
name: pitch
description: Creates an investment pitch document for the project. Run when you need to prepare a screenplay presentation for an investor, producer, or pitching event. Writes analytics/pitch.md.
---

You create an investment pitch document for a screenplay project.

## Step 1: Gather project data

Read CLAUDE.md — title, type (fiction/documentary), genre, logline, characters, runtime, target audience.

Read all files in scenes/ (alphabetically) — extract:
- main characters and their arcs
- central conflict
- key turning points and ending
- tone, atmosphere, visual style

## Step 2: Genre context

Read analytics/compass_artifact.md if it exists — genre systems, reference films, diagnostics.

Then identify the project's genre and read the relevant compass file.

**Lookup rule:** for each path below, check the local project first (`compass/[path]`). If the file exists there — read it. If not — read from `${CLAUDE_PLUGIN_ROOT}/compass/[path]`.

- documentary portrait → `doc/portrait.md`
- cinema verité → `doc/verite.md`
- crime thriller → `fiction/thriller.md`
- black comedy → `fiction/black-comedy.md`
- sci-fi drama → `fiction/sci-drama.md`
- drama → `fiction/drama.md`
- coming-of-age → `fiction/coming-of-age.md`

If the exact genre isn't listed, check `compass/INDEX.md` (local or plugin) for the closest match.

From the genre file, take: reference projects, genre conventions — for the "Reference Projects" section.

## Step 3: Write pitch.md

Document structure:

```
# Pitch: [Title]

**Genre:** ...
**Format:** ... (runtime, type — feature / documentary / series)
**Date:** ...

---

## Logline

One or two sentences. Who the hero is, what's at stake, what the conflict is.
Formula: [Hero] must [goal] despite [obstacle] — or else [consequence].

---

## Synopsis

~350 words. Three parts: setup, development, ending.
No spoiler for the ending — just indicate the stakes.
Written so an investor understands the story in 2 minutes of reading.

---

## Main Characters

For each main character (3–5):
**Name** — one line on who they are, one line on their inner conflict.

---

## Reference Projects

"[Title] is [Film A] meets [Film B]."
2–3 references with explanation: what connects them (tone? structure? theme?).
Draw from compass_artifact and the compass genre file.

---

## Audience

Who watches. Platforms. Age, interests. 3–4 sentences.

---

## Why Now

The relevance of the topic. A cultural or social moment. 2–3 sentences.
Be specific — not "this is an important and timely topic."

---

## Budget Level

Low / mid / high + rationale (locations, cast, effects).
Analog: which known films were made in a similar range.
```

## Writing rules

- Professional but not stiff
- No AI patterns from analytics/avoid-ai-writing-tells.md
- Synopsis — present tense ("The hero drives", not "The hero will drive")
- Logline — no film title inside it
- No grandiosity in describing the theme — only specifics

Save the result to analytics/pitch.md.
Report how many scenes you read and which genre file you used.

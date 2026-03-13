Analyze a scene or the full screenplay. Argument: $ARGUMENTS (scene number, title, or empty).

---

## Mode A — No argument: full screenplay analysis

If `$ARGUMENTS` is empty — analyze the entire screenplay.

1. Read CLAUDE.md — type, title, structure table, characters
2. Read all files in scenes/ in order
3. Check analytics/compass_artifact.md if it exists

### What to check:

**Logic and continuity:**
- Timeline and dates — contradictions, jumps that don't make sense
- Character knowledge — does a character know something they couldn't know yet?
- Location and prop continuity — object appears/disappears, location changes without explanation
- Character motivation gaps — actions without a clear reason

**Genre contract (fiction only):**

Read `${CLAUDE_PLUGIN_ROOT}/compass/fiction/genre-mechanics.md` — find the section for the project's genre. Check:
- Are the **Must happen** obligations present in the screenplay?
- Are any **Forbidden** patterns present?

**Structure — beat check (fiction only):**

Calculate expected beat positions from runtime in CLAUDE.md. Check whether these beats exist and where:

| Beat | Expected position | Found? |
|------|------------------|--------|
| Opening image | ~1% | |
| Catalyst | ~10% | |
| Break into Two | ~20% | |
| Midpoint (false victory/defeat) | ~50% | |
| All is Lost | ~75% | |
| Break into Three | ~85% | |
| Final image | ~99% | |

Also check:
- **Protagonist's dramatic need:** one clear external goal that drives the entire screenplay — can it be stated in one sentence? If not — flag it.
- Does the final image mirror the opening image (transformation visible)?
- Scenes that contribute nothing — no new information, no value change

**Structure — documentary (no beat map, check instead):**
- Is there a clear POV / argument? Or just a sequence of facts?
- Does each block change something — reveal, complicate, or answer?

**Format (check against CLAUDE.md scene formatting rules):**
- Heading format violations
- Missing slug lines (fiction) or missing VIDEO/AUDIO table (documentary)
- Character name formatting errors

**AI writing patterns** (check against `${CLAUDE_PLUGIN_ROOT}/analytics/avoid-ai-writing-tells.md`):
- Rule of threes, emotional placeholders, dialogue that explains feelings

### Output format:

```
FULL ANALYSIS — [Title]
Scenes: N | Est. runtime: N min

LOGIC / CONTINUITY
[issue] → Scene NN: description
...
If none: ✓ No issues found

BEAT CHECK  (fiction only)
Opening image:    scene 01 ✓
Catalyst:         scene 03 ✓  (~10% — on target)
Break into Two:   ✗  (expected ~scene 04)
Midpoint:         scene 09 ✓  (~48% — close)
All is Lost:      ✗  (expected ~scene 14)
Break into Three: ✗
Final image:      ✗
Protagonist goal: [one sentence / unclear — flag]

GENRE CONTRACT  ([genre])
Must happen — present:   [list or ✓ all covered]
Must happen — missing:   [list or none]
Forbidden — violations:  [list or none]

STRUCTURE ISSUES
[issue or observation]
...
If none: ✓ Structure sound

FORMAT ERRORS
Scene NN: description
...
If none: ✓ Format clean

AI PATTERNS
Scene NN: quoted problem line → suggested fix
...
If none: ✓ No AI patterns detected
```

Save nothing. Output only.

---

## Mode B — With argument: single scene analysis

If `$ARGUMENTS` is not empty:

1. Find the file in scenes/ by number or title
2. Read the scene in full
3. Check analytics/compass_artifact.md:
   - If exists — read it (genre systems)
   - If not — warn: "compass_artifact.md not found. Run /compass [genre — logline]. Analysis will continue without genre systems."
4. Score each system from compass (1–10), if compass_artifact.md exists:
   - Charge reversal (+ → - or - → +)?
   - Stakes rising?
   - Visual image without words?
   - Story engine running?
5. Value shift and gap:
   - What is the dominant value at the start of the scene (safety/danger, hope/despair, connection/isolation, truth/lie, power/powerlessness — or other)?
   - What is it at the end?
   - Did the protagonist attempt something and get an unexpected result (gap)? Or did everything go as expected?
   - If no value shift — flag: the scene does not earn its place
5. Check subtext:
   - Does each character say one thing while wanting another? Or do they state their feelings and intentions directly?
   - Is there a surface conflict and a real conflict — or only one?
   - If a character explains their own emotions in dialogue — flag the specific line
6. Check against `${CLAUDE_PLUGIN_ROOT}/analytics/avoid-ai-writing-tells.md` — forbidden patterns?
7. Point out specific problem lines
8. Suggest fixes in BEFORE → AFTER format
9. Answer: can this scene be cut without losing anything? If yes — what exactly would be lost, and can it be conveyed another way?

Save nothing. Analysis and recommendations only.

# Claude Screenplay Plugin

A [Claude Code](https://claude.ai/code) plugin for writing professional screenplays — fiction films, series, and documentary AV-scripts. One plugin, two formats.

---

## Install

In Claude Code:

```
/plugin marketplace add aslanSuleimenov/claude-screenplay-template
/plugin install screenplay@claude-screenplay-template
/reload-plugins
```

---

## Quick start

```bash
# Create a project folder and open it
mkdir my-film && cd my-film
claude

# Initialize — asks 13 questions, creates full structure
/startproject

# Or pass a draft file — Claude extracts what it can, asks only about the rest
/startproject path/to/draft.md
```

`/startproject` creates: `CLAUDE.md`, `scenes/00_title.md`, `analytics/avoid-ai-writing-tells.md`, `memory/`, and `START_HERE.md`.

Genre compass stays in the plugin — no local copy by default. To get editable local copies: `/sync-plugin-files`.

---

## Project types

| | Fiction (screenplay) | Documentary (AV-script) |
|---|---|---|
| Unit | Scene (`# Scene NN:`) | Block (`# Block NN:`) |
| Format | Slug line → action → dialogue | Two-column `\| VIDEO \| AUDIO \|` table |
| DOCX | A4 portrait, Courier New 12pt | A4 landscape, 55%/45% columns |
| Markers | `**INT./EXT.**`, `**CHARACTER**` | `**V/O:**`, `**SOT NAME:**`, `*(NAT SOUND:)*`, `**SUPER:**` |

Type is set once during `/startproject` and drives all commands, hooks, and the converter.

---

## Commands

All auto-detect project type from `CLAUDE.md`.

### Setup

| Command | What it does |
|---------|-------------|
| `/startproject [file]` | Initialize project. Reads file if provided, asks only about missing fields |
| `/split [file]` | Split a draft into scenes/blocks → scenes/ + character tables |
| `/compass [genre — logline]` | Build genre reference from web research → analytics/ |
| `/sync-plugin-files` | Copy compass files and avoid-ai-writing-tells into the project for local editing |

### Write & analyze

| Command | Fiction | Documentary |
|---------|---------|-------------|
| `/new-scene 05 Bar` | Creates scene: slug line + action + dialogue | Creates block: VIDEO/AUDIO table |
| `/rewrite 05 notes` | Rewrites scene by notes | Rewrites block by notes |
| `/analyze 05` | Single scene: compass systems, subtext, value shift | Single block: compass, SOT check |
| `/analyze` | Full script: beats, genre contract, logic, continuity, AI patterns, pacing (dead zones / overload) | Full script: POV, interview structure, logic, pacing |
| `/character-sheet Name` | Arc, voice, wants/needs/says, contradictions | Subject card: appearances, SOT quotes |
| `/continuity` | Time, geography, props, character knowledge, seed | Facts, chronology, names, supers |
| `/research topic` | Web research → analytics/ (sensory details, jargon, counterintuitive facts) | Web research → analytics/ (real cases, SOT candidates, visual evidence) |

### Structure

| Command | What it does |
|---------|-------------|
| `/outline` | Beat sheet with positions (opening image → final image), gap detection |
| `/renumber` | Renumber scenes (two-phase rename, safe on Windows) |
| `/delete-scene NN` | Delete scene + renumber |
| `/merge NN NN` | Merge two scenes |

### Output

| Command | Fiction | Documentary |
|---------|---------|-------------|
| `/stats` | Scenes + runtime + dialogue/action ratio | Blocks + V/O word count + SOT count |
| `/compile` | One-column DOCX (screenplay) | Two-column DOCX (AV-script, landscape) |

### Agents

| Agent | What it does |
|-------|-------------|
| `draft-polish [file]` | Full pipeline: analysis → scenes → logic check → spelling → AI patterns |
| `pitch` | Pitch document for investors/producers → analytics/pitch.md |
| `unico` | UNICO starter pack (passport + character bible + presentation) |
| `proofread [NN\|all]` | Spelling, logic, chronology, anachronisms |

---

## Hooks (automatic)

| Hook | Trigger | Checks |
|------|---------|--------|
| Format + value shift | After every Edit/Write in scenes/ | **Fiction:** slug line, names, indentation, value shift per scene. **Doc:** table, V/O, SOT, SUPER. **Both:** AI writing patterns |
| Compass check | Session start | Warns if compass_artifact.md is missing |
| Session report | Session end | Writes changed scene files to memory/session_log.md |

---

## Genre compass

`compass/` contains genre theory and structural contracts — craft systems and benchmarks, no project-specific content.

```
compass/
├── INDEX.md
├── fiction/
│   ├── genre-mechanics.md    ← structural contracts for 26 genres
│   ├── thriller.md
│   ├── drama.md
│   └── ...26 genres total
└── doc/
    ├── genre-mechanics.md    ← structural contracts for 7 documentary types
    ├── interview-structure.md
    ├── portrait.md
    └── ...7 types total
```

Compass stays in the plugin. Commands read it directly via `${CLAUDE_PLUGIN_ROOT}/compass/`.
To get local editable copies: `/sync-plugin-files`.

Each project gets `analytics/compass_artifact.md` — genre theory applied to that specific project, created by `/compass`.

---

## Folder structure

```
my-film/
  CLAUDE.md                     ← filled by /startproject
  START_HERE.md                 ← quick reference, created by /startproject
  scenes/                       ← scenes/blocks (created by /split or /new-scene)
  analytics/
    avoid-ai-writing-tells.md   ← AI writing pattern checklist (from plugin)
    compass_artifact.md         ← created by /compass
    pitch.md                    ← created by pitch agent
    unico_package.md            ← created by unico agent
  versions/                     ← DOCX output (created by /compile)
  memory/
    session_log.md              ← written by hook automatically
```

---

## Requirements

- [Claude Code](https://claude.ai/code)
- Python 3 + `pip install python-docx` (for `/compile`)

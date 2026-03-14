# Screenplay Plugin — Quick Reference

---

## First time: install the plugin

In Claude Code (any project, one-time):

```
/plugin marketplace add aslanSuleimenov/claude-screenplay-template
/plugin install screenplay@claude-screenplay-template
/reload-plugins
```

Update later: `/plugin update screenplay`

---

## Start a new project

```bash
mkdir "my-film" && cd "my-film"
claude
/startproject
```

Or with an existing draft:
```
/startproject path/to/draft.md
```

Claude extracts what it can from the file and asks only about what's missing.

**What gets created:**
- `CLAUDE.md` — project metadata and formatting rules
- `scenes/00_title.md` — title page
- `analytics/avoid-ai-writing-tells.md` — AI pattern checklist
- `memory/` — session logs
- `START_HERE.md` — this file

Genre compass stays in the plugin. To get local editable copies: `/sync-plugin-files`

---

## Project types

| Type | When | DOCX |
|------|------|------|
| **Fiction** | Feature, series, short | Single-column, Courier New 12pt |
| **Documentary** | Doc, AV-script, corporate | Two-column VIDEO/AUDIO, landscape A4 |

---

## Workflow

```
/startproject → /split [draft] → /compass [genre — logline] → /new-scene → /analyze → /compile
```

---

## Commands

### Setup

| Command | What it does |
|---------|-------------|
| `/startproject [file]` | Initialize. Reads file if provided, asks only about missing fields |
| `/split [file]` | Split a draft into scenes/blocks + fill character tables |
| `/compass [genre — logline]` | Genre reference from web research → analytics/compass_artifact.md |
| `/sync-plugin-files` | Copy compass files into project for local editing |

### Write & analyze

| Command | Fiction | Documentary |
|---------|---------|-------------|
| `/new-scene 05 Bar` | Scene: slug line + action + dialogue | Block: VIDEO/AUDIO table |
| `/rewrite 05 notes` | Rewrite by notes | Rewrite by notes |
| `/analyze 05` | Single scene: compass, subtext, value shift | Single block: compass, SOT |
| `/analyze` | Full script: beats, genre contract, logic, AI patterns | Full script: POV, interview structure, logic |
| `/character-sheet Name` | Arc, voice, wants/needs/says | Subject: appearances, SOT quotes |
| `/continuity` | Time, props, character knowledge, seed | Facts, chronology, title cards |
| `/research topic` | Sensory details, jargon, counterintuitive facts | Real cases, SOT candidates, visual evidence |

### Structure

| Command | What it does |
|---------|-------------|
| `/outline` | Beat sheet with positions, gap detection |
| `/renumber` | Renumber scenes (two-phase rename, safe on Windows) |
| `/delete-scene NN` | Delete + renumber |
| `/merge NN NN` | Merge two scenes |

### Output

| Command | Fiction | Documentary |
|---------|---------|-------------|
| `/stats` | Scenes, runtime, dialogue/action ratio | Blocks, V/O word count, SOT count |
| `/compile` | One-column DOCX | Two-column DOCX (landscape) |
| `/type-check` | Project status: type, compass, scene count | — |

### Agents

| Agent | What it does |
|-------|-------------|
| `draft-polish [file]` | Full pipeline: analysis → scenes → logic → spelling → AI patterns |
| `pitch` | Pitch document → analytics/pitch.md |
| `unico` | UNICO starter pack → analytics/unico_package.md |
| `proofread [NN\|all]` | Spelling, logic, chronology, anachronisms |

---

## Hooks (automatic)

| Hook | When | What it checks |
|------|------|---------------|
| Format + value shift | After every Edit/Write in scenes/ | Slug lines, character names, AI patterns, value shift per scene |
| Compass check | Session start | Warns if compass_artifact.md is missing |
| Session report | Session end | Writes changed files to memory/session_log.md |

---

## Folder structure

```
my-film/
  CLAUDE.md
  START_HERE.md
  scenes/
    00_title.md
  analytics/
    avoid-ai-writing-tells.md
    compass_artifact.md         ← /compass
    pitch.md                    ← pitch agent
    unico_package.md            ← unico agent
  versions/                     ← /compile output
  memory/
    session_log.md
```

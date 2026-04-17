# Workspace Memory Skill

[中文说明](README.zh-CN.md)

A reusable skill for setting up lightweight shared workspace memory with a canonical `AGENTS.md` (plus per-AI entry shims such as `CLAUDE.md` or `GEMINI.md`), `PROJECT_PROGRESS.md`, and `WORKING_MEMORY.md`.

Reusable skill bundle for setting up and maintaining a shared workspace memory system built around:

- `AGENTS.md` — canonical entry file, single source of truth for protocol rules
- `CLAUDE.md`, `GEMINI.md`, `.github/copilot-instructions.md` — optional thin shims that redirect to `AGENTS.md`, added only for AIs actually used in this workspace
- `PROJECT_PROGRESS.md`
- `WORKING_MEMORY.md`
- `archive/project-progress/`
- `memory/grooming-checklist.md`

Codex, OpenAI-style agents, OpenCode, and Cursor read `AGENTS.md` natively, so no shim is needed for those tools.

This repository exposes one skill:

- `$workspace-memory`

## What It Helps With

Use this repository when you want an agent to:

- bootstrap shared workspace memory in a new repo or workspace
- migrate ad hoc notes into a structured memory system
- keep project progress logs useful instead of turning into noise
- separate recent progress from durable working memory
- introduce light archive and grooming rules without overbuilding

## Installation

Install this skill bundle by following the instructions in:

`https://raw.githubusercontent.com/JonnesLin/workspace-memory-skill/refs/heads/main/INSTALL.agent.md`

Typical prompt:

```text
Fetch and follow instructions from https://raw.githubusercontent.com/JonnesLin/workspace-memory-skill/refs/heads/main/INSTALL.agent.md
```

## Using the Skill

After installation, invoke the skill with:

```text
Use $workspace-memory to set up shared memory for this workspace.
```

Examples:

```text
Use $workspace-memory to create AGENTS.md, PROJECT_PROGRESS.md, and WORKING_MEMORY.md for this repo, plus the right per-AI entry shim for the tool I'm using.
```

```text
Use $workspace-memory to audit our current project progress log and working memory, then reorganize them.
```

```text
Use $workspace-memory to add archive and grooming rules without making the system too heavy.
```

```text
Use $workspace-memory to migrate our scattered notes, scratch docs, and session logs into AGENTS.md, PROJECT_PROGRESS.md, and WORKING_MEMORY.md.
```

## Repository Layout

```text
INSTALL.agent.md
.codex/INSTALL.md
skills/workspace-memory/
README.md
README.zh-CN.md
```

Inside the skill:

- `SKILL.md` contains the agent workflow
- `references/protocol.md` contains the detailed operating model
- `assets/workspace-memory/` contains reusable templates

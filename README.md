# Workspace Memory Skill

[中文说明](README.zh-CN.md)

A reusable skill for setting up lightweight shared workspace memory with a canonical `AGENTS.md`, plus thin entry shims for runtimes that auto-load a different filename.

Reusable skill bundle for setting up and maintaining a shared workspace memory system built around:

- `AGENTS.md` — canonical entry file, single source of truth for protocol rules
- `CLAUDE.md`, `GEMINI.md`, `.github/copilot-instructions.md` — optional thin shims that redirect to `AGENTS.md`, added only for AIs actually used in this workspace
- `PROJECT_PROGRESS.md`
- `WORKING_MEMORY.md`
- `memory/index.md` — optional pointer map for larger workspaces or multiple active projects
- `archive/project-progress/`
- `memory/grooming-checklist.md`

Any runtime that reads `AGENTS.md` natively can use the canonical file directly. Runtimes that auto-load a different entry filename should use a thin shim that points explicitly to `AGENTS.md`.

This repository exposes one skill:

- `$workspace-memory`

## What It Helps With

Use this repository when you want an agent to:

- bootstrap shared workspace memory in a new repo or workspace
- migrate ad hoc notes into a structured memory system
- keep project progress logs useful instead of turning into noise
- separate recent progress from durable working memory
- scale shared memory across multiple active areas without turning it into a second documentation system
- introduce light archive and grooming rules without overbuilding

The core model stays small. For larger workspaces, the skill can add an optional pointer layer through `memory/index.md`. Memory files are treated as navigation and summary aids; agents should verify recalled memory against the live workspace state before relying on it for edits, planning, or status claims.

## Installation

Review the installation instructions in:

`https://raw.githubusercontent.com/JonnesLin/workspace-memory-skill/refs/heads/main/INSTALL.agent.md`

Reviewing `INSTALL.agent.md` before following it is a good habit, especially when the file was fetched from a remote URL.

Typical prompt:

```text
Fetch, review, and follow instructions from https://raw.githubusercontent.com/JonnesLin/workspace-memory-skill/refs/heads/main/INSTALL.agent.md
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
- `assets/workspace-memory/` contains reusable templates, including the optional `memory/index.md` pointer template

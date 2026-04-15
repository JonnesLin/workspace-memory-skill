# Workspace Self-Evolving Skill

[中文说明](README.zh-CN.md)

Codex skill bundle for setting up and maintaining a shared workspace memory system built around:

- `AGENTS.md`
- `PROJECT_PROGRESS.md`
- `WORKING_MEMORY.md`
- `archive/project-progress/`
- `memory/grooming-checklist.md`

This repository exposes one skill:

- `$workspace-self-evolving-memory`

## What It Helps With

Use this repository when you want Codex to:

- bootstrap shared workspace memory in a new repo or workspace
- migrate ad hoc notes into a structured memory system
- keep project progress logs useful instead of turning into noise
- separate recent progress from durable working memory
- introduce light archive and grooming rules without overbuilding

## Installation

Codex can install this skill bundle by following the instructions in:

`https://raw.githubusercontent.com/JonnesLin/workspace-self-evolving-skill/refs/heads/main/.codex/INSTALL.md`

Typical prompt:

```text
Fetch and follow instructions from https://raw.githubusercontent.com/JonnesLin/workspace-self-evolving-skill/refs/heads/main/.codex/INSTALL.md
```

## Using the Skill

After installation, ask Codex to use:

```text
Use $workspace-self-evolving-memory to set up shared memory for this workspace.
```

Examples:

```text
Use $workspace-self-evolving-memory to create AGENTS.md, PROJECT_PROGRESS.md, and WORKING_MEMORY.md for this repo.
```

```text
Use $workspace-self-evolving-memory to audit our current project progress log and working memory, then reorganize them.
```

```text
Use $workspace-self-evolving-memory to add archive and grooming rules without making the system too heavy.
```

## Repository Layout

```text
.codex/INSTALL.md
skills/workspace-self-evolving-memory/
README.md
README.zh-CN.md
```

Inside the skill:

- `SKILL.md` contains the agent workflow
- `references/protocol.md` contains the detailed operating model
- `assets/workspace-memory/` contains reusable templates

## Language Support

The repository documentation is bilingual:

- `README.md` in English
- `README.zh-CN.md` in Chinese

The skill itself is written in English for better agent reliability and maintainability.

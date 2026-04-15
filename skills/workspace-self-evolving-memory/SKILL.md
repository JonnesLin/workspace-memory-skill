---
name: workspace-self-evolving-memory
description: Use when Codex needs to set up, audit, migrate, or maintain a shared workspace memory system built around AGENTS.md, PROJECT_PROGRESS.md, and WORKING_MEMORY.md, especially when project context is being lost across sessions, logs are getting noisy, or a team wants lightweight archive and grooming rules without overbuilding.
---

# Workspace Self Evolving Memory

## Overview

Set up and maintain a lightweight shared memory system for a workspace. Keep startup context cheap by separating recent project progress from durable working memory, then archive and groom only where it materially improves signal.

## Workflow

### 1. Establish the target scope

Identify whether the memory system is:

- workspace-wide
- repo-specific
- a migration from an existing ad hoc note system

Default to one shared workspace memory system unless the user asks for finer-grained memory boundaries.

### 2. Use the standard root layout

Keep these files at the workspace root:

- `AGENTS.md`
- `PROJECT_PROGRESS.md`
- `WORKING_MEMORY.md`

Create these supporting paths only when useful:

- `archive/project-progress/`
- `memory/grooming-checklist.md`

Do not hide the high-frequency files in a subdirectory. The entrypoint files should stay easy to discover.

### 3. Separate responsibilities cleanly

Use:

- `AGENTS.md` for protocol and read/write rules
- `PROJECT_PROGRESS.md` for reverse-chronological recent progress
- `WORKING_MEMORY.md` for curated durable memory

Do not turn `WORKING_MEMORY.md` into a session log. Do not turn `PROJECT_PROGRESS.md` into a general handbook.

### 4. Prefer templates over blank pages

If the workspace does not already have memory files, start from the templates in:

- `assets/workspace-memory/AGENTS.md`
- `assets/workspace-memory/PROJECT_PROGRESS.md`
- `assets/workspace-memory/WORKING_MEMORY.md`
- `assets/workspace-memory/memory/grooming-checklist.md`

Copy and adapt them to the workspace instead of rewriting the structure from scratch.

### 5. Keep the progress log easy to scan

Add a short `Current Snapshot` section to the top of `PROJECT_PROGRESS.md` when the workspace is active enough to benefit from it.

Use archive only for older progress history. Archive by default should apply to `PROJECT_PROGRESS.md`, not `WORKING_MEMORY.md`.

### 6. Groom lightly and regularly

When the system gets noisy:

- move old progress entries into `archive/project-progress/`
- compress repeated monitoring entries into one summary
- merge duplicate working-memory rules
- delete stale assumptions

Do not introduce a heavy maintenance ritual if the current files are still cheap to scan.

## Reference

Read `references/protocol.md` when you need the detailed operating model, archive rules, or default read/write path.

## Resources (optional)

### references/
Read `references/protocol.md` for the detailed design and maintenance rules.

### assets/
Use `assets/workspace-memory/` as the copyable baseline structure for a new workspace memory setup.

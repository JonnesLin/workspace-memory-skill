---
name: workspace-memory
description: Use when an agent needs to set up, audit, migrate, or maintain a shared workspace memory system built around a canonical AGENTS.md (plus per-AI entry shims such as CLAUDE.md or GEMINI.md), PROJECT_PROGRESS.md, and WORKING_MEMORY.md, especially when project context is being lost across sessions, logs are getting noisy, or a team wants lightweight archive and grooming rules without overbuilding.
---

# Workspace Memory

## Overview

Set up and maintain a lightweight shared memory system for a workspace. Keep startup context cheap by separating recent project progress from durable working memory. Use one canonical entry file (`AGENTS.md`) as the single source of truth, and add thin per-AI shim files only for runtimes whose auto-loaded filename differs.

## Workflow

### 1. Establish the target scope

Identify whether the memory system is:

- workspace-wide
- repo-specific
- a migration from an existing ad hoc note system

Default to one shared workspace memory system unless the user asks for finer-grained memory boundaries.

### 2. Use the standard root layout

Keep these files at the workspace root:

- `AGENTS.md` — canonical entry file (the only full-content entry file)
- `PROJECT_PROGRESS.md`
- `WORKING_MEMORY.md`

Add per-AI entry shims only when the invoking AI reads a different default filename. Each shim is a one-line redirect to `AGENTS.md` so there is still a single source of truth.

Create these supporting paths only when useful:

- `archive/project-progress/`
- `memory/index.md`
- `memory/grooming-checklist.md`

Do not hide the high-frequency files in a subdirectory. The entrypoint files should stay easy to discover.

For larger workspaces or multiple active projects, `memory/index.md` is an optional pointer map. Use it to route agents to active subtrees, project docs, or project-specific memory files when the target is not obvious. Keep it pointer-oriented; do not duplicate current status from `PROJECT_PROGRESS.md` or durable rules from `WORKING_MEMORY.md`.

### 3. Pick the right entry file for the invoking AI

Use the mapping below to decide which entry file the current AI auto-loads. Write a shim only when the AI's filename is not `AGENTS.md`.

| AI / Tool | Auto-loaded entry file | Action |
| --- | --- | --- |
| Codex / OpenAI-style agents | `AGENTS.md` | Canonical file; no shim needed |
| OpenCode | `AGENTS.md` | Canonical file; no shim needed |
| Cursor | `AGENTS.md` (natively supported) | Canonical file; no shim needed |
| Claude Code | `CLAUDE.md` | Write `CLAUDE.md` shim redirecting to `AGENTS.md` |
| Gemini CLI | `GEMINI.md` | Write `GEMINI.md` shim redirecting to `AGENTS.md` |
| GitHub Copilot (IDE / coding agent) | `.github/copilot-instructions.md` | Write shim at that path redirecting to `AGENTS.md` |

Detection order:

1. If you can identify the invoking AI from runtime signals (tool name in the environment, system prompt identity, CLI harness), use that.
2. If more than one AI is actively used in this workspace, create a shim for each AI that needs one.
3. If the invoking AI is unclear, ask the user which AIs this workspace should support before writing shims.
4. Do not silently default to writing every shim. Fewer files are better.

Some runtimes are weaker at following multi-file indirection. In those cases, the shim should explicitly tell the agent to read `AGENTS.md` and, for non-trivial tasks, `PROJECT_PROGRESS.md` and `WORKING_MEMORY.md`, rather than assuming the agent will infer the next hop.

### 4. Separate responsibilities cleanly

Use:

- `AGENTS.md` for protocol and read/write rules
- optional `memory/index.md` for navigation pointers only
- `PROJECT_PROGRESS.md` for reverse-chronological recent progress
- `WORKING_MEMORY.md` for curated durable memory

Do not turn `WORKING_MEMORY.md` into a session log. Do not turn `PROJECT_PROGRESS.md` into a general handbook. Do not let `memory/index.md` become a second status log. Do not duplicate `AGENTS.md` content into the shim files.

### 5. Verify memory before relying on it

Treat `PROJECT_PROGRESS.md`, `WORKING_MEMORY.md`, and any optional pointer file as working memory, not as ground truth.

Before using recalled memory to make edits, status claims, or planning decisions:

- verify the relevant fact against the current files, code, or repo state
- update or remove stale memory when the live workspace disagrees
- prefer the live workspace state over memory when they conflict

### 6. Prefer templates over blank pages

If the workspace does not already have memory files, start from the templates in:

- `assets/workspace-memory/AGENTS.md`
- `assets/workspace-memory/PROJECT_PROGRESS.md`
- `assets/workspace-memory/WORKING_MEMORY.md`
- `assets/workspace-memory/memory/index.md`
- `assets/workspace-memory/memory/grooming-checklist.md`

For each needed shim, start from the matching template in `assets/workspace-memory/shims/` (for example `CLAUDE.md`, `GEMINI.md`, `.github/copilot-instructions.md`). Copy each shim to the target path shown in the §3 mapping table, and adapt it to the workspace instead of rewriting the structure from scratch.

### 7. Respect existing entry files

If the workspace already has a file at a target path:

- Do not overwrite it.
- Amend it so it points to `AGENTS.md` as the canonical entry file, while preserving prior content.
- If the existing file already contains the full protocol, leave it in place and only reconcile obvious drift.

### 8. Keep the progress log easy to scan

Add a short `Current Snapshot` section to the top of `PROJECT_PROGRESS.md` when the workspace is active enough to benefit from it.

Use archive only for older progress history. Archive by default should apply to `PROJECT_PROGRESS.md`, not `WORKING_MEMORY.md`.

### 9. Groom lightly and regularly

When the system gets noisy:

- move old progress entries into `archive/project-progress/`
- trim or rewrite stale pointers in `memory/index.md`
- compress repeated monitoring entries into one summary
- merge duplicate working-memory rules
- delete stale assumptions
- remove shim files for AIs that are no longer used in this workspace

Do not introduce a heavy maintenance ritual if the current files are still cheap to scan.

## Reference

Read `references/protocol.md` when you need the detailed operating model, archive rules, shim semantics, or default read/write path.

## Resources (optional)

### references/
Read `references/protocol.md` for the detailed design and maintenance rules.

### assets/
Use `assets/workspace-memory/` as the copyable baseline structure for a new workspace memory setup. Use `assets/workspace-memory/shims/` for per-AI entry shims and `assets/workspace-memory/memory/index.md` when the workspace needs a pointer layer.

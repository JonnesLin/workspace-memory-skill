# Workspace Memory Protocol

Use this reference when setting up, auditing, or refactoring a workspace memory system.

## Core Goals

- Keep startup context cheap.
- Preserve recent project state.
- Preserve durable lessons separately from session logs.
- Avoid turning memory into a second documentation system.
- Keep protocol rules in exactly one file and let per-AI entry files redirect to it.

## Recommended Root Layout

```text
<workspace-root>/
  AGENTS.md              # canonical entry file
  CLAUDE.md              # optional shim, only if Claude Code is used
  GEMINI.md              # optional shim, only if Gemini CLI is used
  .github/
    copilot-instructions.md   # optional shim, only if GitHub Copilot is used
  PROJECT_PROGRESS.md
  WORKING_MEMORY.md
  archive/
    project-progress/
  memory/
    grooming-checklist.md
```

## Entry File Model

### Canonical file

Use `AGENTS.md` as the single source of truth for protocol and read/write rules. Codex, OpenAI-style agents, OpenCode, and Cursor all auto-load it by default.

### Per-AI shims

Some AIs auto-load a different default filename. For each such AI that is actually used in the workspace, create a thin shim that redirects to `AGENTS.md`:

| AI | Shim path | Role |
| --- | --- | --- |
| Claude Code | `CLAUDE.md` | Redirect to `AGENTS.md` |
| Gemini CLI | `GEMINI.md` | Redirect to `AGENTS.md` |
| GitHub Copilot (IDE / coding agent) | `.github/copilot-instructions.md` | Redirect to `AGENTS.md` |

Shim rules:

- Keep each shim to a short pointer plus an empty overrides section.
- Do not copy the canonical protocol into a shim.
- Only create shims for AIs that are actually used in this workspace.
- Delete unused shims during grooming.

## File Responsibilities

### Canonical entry file (`AGENTS.md`)

Use as the workspace entrypoint.

Store:

- session start protocol
- session closeout protocol
- rules for when memory must be read
- rules for when memory should be updated

Do not store long project facts here.

### `PROJECT_PROGRESS.md`

Use as a reverse-chronological session log.

Store:

- affected project or path
- what changed
- problems
- resolutions
- open items
- next steps

Prefer a short `Current Snapshot` section at the top for the active project, blocker, latest decision, and next likely step.

### `WORKING_MEMORY.md`

Use as curated durable memory.

Store only information that is still worth reading in future sessions:

- stable user preferences
- workspace-wide constraints
- recurring pitfalls and proven resolutions
- durable project assumptions that still matter

Do not use it as a time-series log.

## Archive Policy

Archive only `PROJECT_PROGRESS.md` by default.

Move old log entries into `archive/project-progress/` when one or more of these are true:

- the active log has become expensive to scan
- an old phase is closed and mostly historical
- older entries no longer belong in default startup context

Do not create a separate archive for `WORKING_MEMORY.md` unless there is a strong, demonstrated need. Usually it should be rewritten and trimmed instead.

## Grooming Policy

### Progress log grooming

- keep recent and active entries in the main file
- move old entries into archive
- compress repeated monitoring entries into one summary when possible

### Working memory grooming

- merge duplicates
- delete expired rules
- rewrite session-specific notes into durable lessons
- remove notes that no longer change future behavior

### Shim grooming

- remove shim files for AIs that are no longer used in this workspace
- check that each remaining shim still points to the canonical entry file and has not drifted into duplicated protocol text

## Default Read Path

For non-trivial tasks:

1. Read the canonical entry file (`AGENTS.md`); treat any per-AI shim as a redirect only.
2. Read the top snapshot in `PROJECT_PROGRESS.md`.
3. Read the recent relevant progress entries.
4. Read `WORKING_MEMORY.md`.
5. Read archive only if current files do not explain the needed history.

## Default Write Path

Before finishing a non-trivial session:

1. Decide whether project state changed enough to update `PROJECT_PROGRESS.md`.
2. Decide whether a durable lesson emerged that belongs in `WORKING_MEMORY.md`.
3. Decide whether the progress log should be trimmed or archived.

## Language Guidance

If the workspace has no stronger preference, use:

- English for shared memory files
- the user's language for conversational responses

## Failure Modes To Avoid

- putting every session detail into `WORKING_MEMORY.md`
- archiving too early and hiding active context
- storing policies in three different files
- duplicating the canonical protocol into every per-AI shim
- creating shims for AIs that are not actually used in this workspace
- treating memory as a hard gate instead of a useful operating aid
- keeping old progress in the main file until startup becomes slow and noisy

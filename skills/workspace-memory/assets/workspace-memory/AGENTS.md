# Workspace Agent Instructions

This is the canonical entry file for every session in this workspace.

Other per-AI entry files in this workspace (for example `CLAUDE.md` or `GEMINI.md`) are thin shims that redirect here. Keep protocol rules in this file only.

For non-trivial tasks, read the following files before doing project-specific reasoning, planning, implementation, debugging, or status reporting:

- `PROJECT_PROGRESS.md`
- `WORKING_MEMORY.md`

If the workspace uses `memory/index.md` and the target project or area is not obvious, read it before project-specific work.

## Scope

- These instructions apply to the entire workspace root.
- The memory files are shared across projects in this workspace.
- Always identify the target project or path before doing project-specific work.

## Session Start Protocol

For any non-trivial task:

1. Read `PROJECT_PROGRESS.md`.
2. Read `WORKING_MEMORY.md`.
3. If `memory/index.md` exists and the target project or area is unclear, read it.
4. Identify the target project or subdirectory.
5. Use the relevant memory files to align with recent progress, open issues, preferences, and constraints.

You may skip steps 1 and 2 only for tasks that are clearly context-free, such as:

- pure translation
- isolated rewriting or formatting
- a one-off shell command with no project impact
- casual Q and A unrelated to the workspace

## During the Session

- Use `PROJECT_PROGRESS.md` to understand recent work, resolved issues, open problems, and likely next steps.
- Use `WORKING_MEMORY.md` to understand durable preferences, workflow habits, project constraints, and reusable lessons.
- Use `memory/index.md` only as a pointer map when the workspace is large enough to need routing help.
- Treat memory as a summary layer, not as ground truth. Verify recalled facts against the live workspace before relying on them for edits, plans, or status claims.
- Prefer concise summaries and durable decisions over raw transcript-style notes.

## Session Closeout

Before claiming completion for any non-trivial session:

1. Decide whether `PROJECT_PROGRESS.md` should be updated.
2. Decide whether `WORKING_MEMORY.md` should be updated.
3. Update the files when the session created useful memory for future sessions.

If neither file needs a change, do not add filler just to satisfy the process.

## Update Rules

Update `PROJECT_PROGRESS.md` when:

- project state changed
- meaningful investigation happened
- a bug or blocker was resolved
- a decision clarified the current state or next step
- planning or architecture materially changed project direction

Update `WORKING_MEMORY.md` only when the session revealed durable information such as:

- user preferences
- project-wide constraints
- workflow habits
- naming or style expectations
- recurring pitfalls and proven resolutions

## Writing Rules

- Write shared memory content in English unless the workspace specifies otherwise.
- Preserve prior entries in `PROJECT_PROGRESS.md` and add each new session entry at the top of the log.
- Include the affected project or path in each progress entry.
- In progress entries, record what changed, what was solved, what problems appeared, and what remains next.
- Keep `WORKING_MEMORY.md` curated and deduplicated rather than chronological.
- Record both the problem and the solution when the lesson is reusable.

## Archive And Grooming

- Keep this canonical entry file, `PROJECT_PROGRESS.md`, and `WORKING_MEMORY.md` at the workspace root.
- Use `memory/index.md` only when the workspace is large or has multiple active areas.
- Keep any per-AI entry shims thin; do not duplicate these rules into them.
- Archive older progress entries under `archive/project-progress/` when the main log becomes noisy.
- Use `memory/grooming-checklist.md` for periodic cleanup.

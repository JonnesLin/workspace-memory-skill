# Workspace Index

Use this file only when the workspace is large enough that agents need a pointer map.

## Purpose

- point to active projects or subtrees
- tell agents where to start reading
- link to project-specific docs or memory files
- keep startup routing cheap without duplicating full status

## Active Areas

Use short entries such as:

| Path | Purpose | Read First | Notes |
| --- | --- | --- | --- |
| `apps/mobile` | iOS app | `apps/mobile/README.md`, `PROJECT_PROGRESS.md` | Active this week |
| `services/api` | Backend API | `services/api/AGENTS.md`, `services/api/docs/architecture.md` | Needs auth cleanup |

## Rules

- Keep entries short and pointer-oriented.
- Do not duplicate current status that belongs in `PROJECT_PROGRESS.md`.
- Do not duplicate durable rules that belong in `WORKING_MEMORY.md`.
- Remove stale entries when a project is no longer active.
- If the target project is already obvious, agents can skip this file.

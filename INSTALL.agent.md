# AI Installation Instructions for Workspace Memory Skill

This file is the unified installation and update entrypoint for AI agents.

## Goal

Install or update `workspace-memory` for the current platform, using the platform-native layout when possible.

## General Rules

1. Detect the current platform first. Prefer runtime or tooling context over filesystem guessing.
2. Prefer updating an existing installation over creating a second copy.
3. Prefer a full-repo install when the platform supports repo-based extensions or native skill folders.
4. Only use a manual fallback when the platform is unclear or cannot activate the skill directly.
5. Do not delete unrelated files or directories. If an activation symlink is wrong, replace only that symlink.
6. After finishing, report:
   - installed repo path
   - active branch
   - current commit hash
   - activation path used by the platform
   - whether the user needs to restart the tool

## Repository

- Repo URL: `https://github.com/JonnesLin/workspace-memory-skill.git`
- Default branch: `main`
- Skill name: `workspace-memory`

## Platform Detection Order

Follow the first branch that clearly matches the current environment.

### Codex

Use this branch if you are running inside Codex or the environment clearly uses Codex conventions.

1. Install or update the repo at `~/.codex/workspace-memory-skill`
2. Ensure the activation path exists:
   `~/.agents/skills/workspace-memory -> ~/.codex/workspace-memory-skill/skills/workspace-memory`
3. For Codex-specific details, follow the instructions in:
   `.codex/INSTALL.md`
4. Tell the user to restart Codex after installation or update

### Claude Code

Use this branch if you are running inside Claude Code or the environment clearly uses Claude conventions.

1. Install or update the repo at `~/.claude/plugins/repos/workspace-memory-skill`
2. Ensure the activation path exists:
   `~/.claude/skills/workspace-memory -> ~/.claude/plugins/repos/workspace-memory-skill/skills/workspace-memory`
3. If the activation path exists but is not a symlink to the repo skill directory, repair only that path
4. Tell the user to restart Claude Code after installation or update

### Unknown or Mixed Environment

If the environment is unclear:

1. Say which signals were ambiguous
2. Prefer a conservative full-repo clone to a neutral path such as `~/workspace-memory-skill`
3. If the runtime has a known skill directory, link `skills/workspace-memory` into it
4. Do not pretend activation is complete unless you can verify the platform activation path

## Update Policy

When you find an existing repo clone at the platform's expected path:

1. Enter that repo
2. Run `git pull --ff-only`
3. Repair activation links only if they are missing or incorrect

## Verification

Before claiming success, verify:

1. The repo exists at the expected path
2. `git branch --show-current` returns the active branch
3. `git rev-parse --short HEAD` returns a commit hash
4. The platform activation path exists and points to the expected skill directory

## Optional Global Hint

After installation or update, you may offer to add a global hint to the user's user-level `AGENTS.md` or `CLAUDE.md`.

Rules:

1. Ask first. Do not modify those files without explicit user approval.
2. Present it as optional.
3. Describe it as a way to help future agents know when to use this skill and where to fetch installation or update instructions if needed.
4. Do not describe it as permission for silent background updates.

Suggested question:

```text
Do you want me to add a global hint to your user-level AGENTS.md / CLAUDE.md so future agents know when to use `workspace-memory` and where to fetch install or update instructions if needed?
```

Suggested snippet:

```text
When a workspace starts losing context across sessions, or when AGENTS.md / PROJECT_PROGRESS.md / WORKING_MEMORY.md need to be set up or reorganized, prefer the installed `workspace-memory` skill.

If `workspace-memory` is missing or appears outdated, fetch and follow instructions from:
https://raw.githubusercontent.com/JonnesLin/workspace-memory-skill/refs/heads/main/INSTALL.agent.md
```

## Final Report

Report the result in this format:

- Platform detected: `...`
- Repo path: `...`
- Branch: `...`
- Commit: `...`
- Activation path: `...`
- Restart required: `yes` or `no`

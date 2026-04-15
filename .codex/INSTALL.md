# Codex Installation Instructions for Workspace Memory Skill

Use this file only when the current platform is Codex. The unified entrypoint for agents is `INSTALL.agent.md`.

## Goal

Install or update `workspace-memory` in the standard Codex layout.

## Paths

- Repo path: `~/.codex/workspace-memory-skill`
- Skill path inside repo: `~/.codex/workspace-memory-skill/skills/workspace-memory`
- Activation path: `~/.agents/skills/workspace-memory`

## Install Or Update

1. **Install or update the repo:**

```bash
if [ -d ~/.codex/workspace-memory-skill/.git ]; then
  git -C ~/.codex/workspace-memory-skill pull --ff-only
else
  mkdir -p ~/.codex
  git clone https://github.com/JonnesLin/workspace-memory-skill.git ~/.codex/workspace-memory-skill
fi
```

2. **Create or repair the skill symlink:**

```bash
mkdir -p ~/.agents/skills
if [ -L ~/.agents/skills/workspace-memory ]; then
  rm ~/.agents/skills/workspace-memory
elif [ -e ~/.agents/skills/workspace-memory ]; then
  echo "~/.agents/skills/workspace-memory exists and is not a symlink; inspect it manually."
  exit 1
fi
ln -s ~/.codex/workspace-memory-skill/skills/workspace-memory ~/.agents/skills/workspace-memory
```

**Windows (PowerShell):**

```powershell
if (Test-Path "$env:USERPROFILE\.codex\workspace-memory-skill\.git") {
  git -C "$env:USERPROFILE\.codex\workspace-memory-skill" pull --ff-only
} else {
  New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.codex" | Out-Null
  git clone https://github.com/JonnesLin/workspace-memory-skill.git "$env:USERPROFILE\.codex\workspace-memory-skill"
}

New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.agents\skills" | Out-Null
if (Test-Path "$env:USERPROFILE\.agents\skills\workspace-memory") {
  $item = Get-Item "$env:USERPROFILE\.agents\skills\workspace-memory"
  if (-not $item.LinkType) {
    throw "$env:USERPROFILE\.agents\skills\workspace-memory exists and is not a link; inspect it manually."
  }
  Remove-Item "$env:USERPROFILE\.agents\skills\workspace-memory" -Force
}
cmd /c mklink /J "$env:USERPROFILE\.agents\skills\workspace-memory" "$env:USERPROFILE\.codex\workspace-memory-skill\skills\workspace-memory"
```

3. **Restart Codex** after installation or update.

## Verify

Run:

```bash
git -C ~/.codex/workspace-memory-skill branch --show-current
git -C ~/.codex/workspace-memory-skill rev-parse --short HEAD
ls -la ~/.agents/skills/workspace-memory
```

Expected:

- branch is `main`
- a short commit hash is printed
- `~/.agents/skills/workspace-memory` points to `~/.codex/workspace-memory-skill/skills/workspace-memory`

## Use

After restart, try:

```text
Use $workspace-memory to set up shared memory for this workspace.
```

## Uninstall

```bash
rm ~/.agents/skills/workspace-memory
```

Optionally remove the repo clone:

```bash
rm -rf ~/.codex/workspace-memory-skill
```

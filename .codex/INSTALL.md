# Installing Workspace Memory Skill

Install the workspace memory skill through native skill discovery.

## Prerequisites

- Git

## Installation

1. **Clone the repository:**

```bash
git clone https://github.com/JonnesLin/workspace-memory-skill.git ~/.codex/workspace-memory-skill
```

2. **Create the skills symlink:**

```bash
mkdir -p ~/.agents/skills
ln -s ~/.codex/workspace-memory-skill/skills ~/.agents/skills/workspace-memory-skill
```

**Windows (PowerShell):**

```powershell
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.agents\skills"
cmd /c mklink /J "$env:USERPROFILE\.agents\skills\workspace-memory-skill" "$env:USERPROFILE\.codex\workspace-memory-skill\skills"
```

3. **Restart your agent runtime** to discover the skill bundle.

## Verify

```bash
ls -la ~/.agents/skills/workspace-memory-skill
```

You should see a symlink (or junction on Windows) pointing to this repository's `skills` directory.

## Use

After restart, try:

```text
Use $workspace-memory to set up shared memory for this workspace.
```

## Updating

```bash
cd ~/.codex/workspace-memory-skill && git pull
```

Updates become available through the symlink after the next runtime launch.

## Uninstalling

```bash
rm ~/.agents/skills/workspace-memory-skill
```

Optionally remove the clone:

```bash
rm -rf ~/.codex/workspace-memory-skill
```

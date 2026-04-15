# Installing Workspace Self-Evolving Skill

Install the workspace memory skill through native skill discovery.

## Prerequisites

- Git

## Installation

1. **Clone the repository:**

```bash
git clone https://github.com/JonnesLin/workspace-self-evolving-skill.git ~/.codex/workspace-self-evolving-skill
```

2. **Create the skills symlink:**

```bash
mkdir -p ~/.agents/skills
ln -s ~/.codex/workspace-self-evolving-skill/skills ~/.agents/skills/workspace-self-evolving-skill
```

**Windows (PowerShell):**

```powershell
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.agents\skills"
cmd /c mklink /J "$env:USERPROFILE\.agents\skills\workspace-self-evolving-skill" "$env:USERPROFILE\.codex\workspace-self-evolving-skill\skills"
```

3. **Restart your agent runtime** to discover the skill bundle.

## Verify

```bash
ls -la ~/.agents/skills/workspace-self-evolving-skill
```

You should see a symlink (or junction on Windows) pointing to this repository's `skills` directory.

## Use

After restart, try:

```text
Use $workspace-self-evolving-memory to set up shared memory for this workspace.
```

## Updating

```bash
cd ~/.codex/workspace-self-evolving-skill && git pull
```

Updates become available through the symlink after the next runtime launch.

## Uninstalling

```bash
rm ~/.agents/skills/workspace-self-evolving-skill
```

Optionally remove the clone:

```bash
rm -rf ~/.codex/workspace-self-evolving-skill
```

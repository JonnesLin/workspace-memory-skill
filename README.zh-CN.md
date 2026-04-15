# Workspace Memory Skill

[English README](README.md)

这是一个通用的 workspace memory skill 仓库，用来为工作区建立和维护一套共享记忆系统，核心围绕下面这些文件和目录：

- `AGENTS.md`
- `PROJECT_PROGRESS.md`
- `WORKING_MEMORY.md`
- `archive/project-progress/`
- `memory/grooming-checklist.md`

这个仓库当前提供一个 skill：

- `$workspace-memory`

## 它解决什么问题

当你希望 agent 做下面这些事情时，可以用这个仓库：

- 在新 workspace 或 repo 里初始化共享 memory 体系
- 把零散笔记迁移成结构化的 memory 系统
- 让项目进展日志保持可读，而不是不断膨胀成噪音
- 区分近期进展和长期有效的 working memory
- 在不过度设计的前提下，引入 archive 和定期整理机制

## 安装方式

可以直接读取下面这个安装说明：

`https://raw.githubusercontent.com/JonnesLin/workspace-memory-skill/refs/heads/main/.codex/INSTALL.md`

典型提示词：

```text
Fetch and follow instructions from https://raw.githubusercontent.com/JonnesLin/workspace-memory-skill/refs/heads/main/.codex/INSTALL.md
```

## 使用方式

安装完成后，可以直接这样调用：

```text
Use $workspace-memory to set up shared memory for this workspace.
```

也可以这样说：

```text
Use $workspace-memory to create AGENTS.md, PROJECT_PROGRESS.md, and WORKING_MEMORY.md for this repo.
```

```text
Use $workspace-memory to audit our current project progress log and working memory, then reorganize them.
```

```text
Use $workspace-memory to add archive and grooming rules without making the system too heavy.
```

## 仓库结构

```text
.codex/INSTALL.md
skills/workspace-memory/
README.md
README.zh-CN.md
```

其中 skill 内部包含：

- `SKILL.md`：agent 执行流程
- `references/protocol.md`：详细协议和设计边界
- `assets/workspace-memory/`：可复用模板文件

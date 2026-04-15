# Workspace Memory Skill

[English README](README.md)

一个用 `AGENTS.md`、`PROJECT_PROGRESS.md` 和 `WORKING_MEMORY.md` 为工作区建立轻量共享记忆体系的通用 skill。

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
使用 $workspace-memory 为这个 workspace 搭建共享 memory 系统。
```

也可以这样说：

```text
使用 $workspace-memory 为这个仓库创建 AGENTS.md、PROJECT_PROGRESS.md 和 WORKING_MEMORY.md。
```

```text
使用 $workspace-memory 审查我们当前的 project progress log 和 working memory，然后重新整理它们。
```

```text
使用 $workspace-memory 给这套系统加上 archive 和 grooming 规则，但不要把它做得太重。
```

```text
使用 $workspace-memory 把我们零散的 notes、scratch docs 和 session logs 迁移进 AGENTS.md、PROJECT_PROGRESS.md 和 WORKING_MEMORY.md。
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

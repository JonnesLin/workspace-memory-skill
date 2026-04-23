# Workspace Memory Skill

[English README](README.md)

一个用规范入口 `AGENTS.md` 搭配薄入口 shim，为工作区建立轻量共享记忆体系的通用 skill。对于会自动读取其他入口文件名的运行时，可以用 shim 转发回 `AGENTS.md`。

这是一个通用的 workspace memory skill 仓库，用来为工作区建立和维护一套共享记忆系统，核心围绕下面这些文件和目录：

- `AGENTS.md`：规范入口文件，协议规则的唯一真源
- `CLAUDE.md`、`GEMINI.md`、`.github/copilot-instructions.md`：可选的薄 shim，只转发到 `AGENTS.md`，只为实际使用的 AI 创建
- `PROJECT_PROGRESS.md`
- `WORKING_MEMORY.md`
- `memory/index.md`：可选的指针文件，用于更大的工作区或多活项目
- `archive/project-progress/`
- `memory/grooming-checklist.md`

任何原生支持读取 `AGENTS.md` 的运行时都可以直接使用规范入口。会自动读取其他文件名的运行时，则应使用一个明确指向 `AGENTS.md` 的薄 shim。

这个仓库当前提供一个 skill：

- `$workspace-memory`

## 它解决什么问题

当你希望 agent 做下面这些事情时，可以用这个仓库：

- 在新 workspace 或 repo 里初始化共享 memory 体系
- 把零散笔记迁移成结构化的 memory 系统
- 让项目进展日志保持可读，而不是不断膨胀成噪音
- 区分近期进展和长期有效的 working memory
- 在多个活跃目录之间扩展共享 memory，而不把它做成第二套文档系统
- 在不过度设计的前提下，引入 archive 和定期整理机制

核心模型仍然保持轻量。对于更大的工作区，可以额外加上 `memory/index.md` 作为指针层。memory 文件应被视为导航和摘要辅助，agent 在依赖其中的回忆来做修改、规划或状态判断前，应先和当前工作区真实状态核对。

## 安装方式

先阅读下面的安装说明：

`https://raw.githubusercontent.com/JonnesLin/workspace-memory-skill/refs/heads/main/INSTALL.agent.md`

尤其当这个文件是从远程 URL 抓取下来的时候，先 review 再照着执行会更稳妥。

典型提示词：

```text
Fetch, review, and follow instructions from https://raw.githubusercontent.com/JonnesLin/workspace-memory-skill/refs/heads/main/INSTALL.agent.md
```

## 使用方式

安装完成后，可以直接这样调用：

```text
使用 $workspace-memory 为这个 workspace 搭建共享 memory 系统。
```

也可以这样说：

```text
使用 $workspace-memory 为这个仓库创建 AGENTS.md、PROJECT_PROGRESS.md 和 WORKING_MEMORY.md，并为我当前用的 AI 生成对应的入口 shim。
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
INSTALL.agent.md
.codex/INSTALL.md
skills/workspace-memory/
README.md
README.zh-CN.md
```

其中 skill 内部包含：

- `SKILL.md`：agent 执行流程
- `references/protocol.md`：详细协议和设计边界
- `assets/workspace-memory/`：可复用模板文件，包含可选的 `memory/index.md` 指针模板

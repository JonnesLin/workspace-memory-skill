# Workspace Memory Platform-Neutral Documentation Update Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Make the workspace-memory skill platform-neutral in framing, safer in installation guidance, and more durable at scale by adding optional index/pointer guidance and a verify-before-recall rule.

**Architecture:** Keep the existing three-file memory model unchanged. Update user-facing docs and the skill/protocol definitions so they describe capabilities instead of favoring one runtime, add an optional navigation layer for larger workspaces, and state that memory is a hint source that must be verified against the live workspace before being treated as current truth.

**Tech Stack:** Markdown documentation, repository conventions, ripgrep verification

---

### Task 1: Plan the wording changes

**Files:**
- Modify: `README.md`
- Modify: `INSTALL.agent.md`
- Modify: `skills/workspace-memory/SKILL.md`
- Modify: `skills/workspace-memory/references/protocol.md`

- [ ] **Step 1: Confirm current wording and target sections**

Run: `rg -n "Codex|AGENTS.md|Fetch and follow|stale|Current Snapshot|archive" README.md INSTALL.agent.md skills/workspace-memory/SKILL.md skills/workspace-memory/references/protocol.md`
Expected: Matches showing current platform framing, install prompt language, and memory-maintenance rules.

- [ ] **Step 2: Define the edits**

Apply these changes:

```text
README.md:
- describe the skill as working across agents that support AGENTS.md directly or via thin shim files
- replace the installation prompt with fetch-review-follow guidance
- mention optional index/pointer files and verify-before-recall behavior

INSTALL.agent.md:
- replace "fetch and follow" phrasing in the optional global hint with a review step
- keep platform branches, but frame them as runtime-specific install flows rather than a favored default

SKILL.md and references/protocol.md:
- keep AGENTS.md / PROJECT_PROGRESS.md / WORKING_MEMORY.md as the core model
- add an optional index/pointer layer for larger workspaces or multiple active projects
- add a verify-before-recall rule so memory is used as a lead, not a fact source
- strengthen shim guidance for runtimes that may not reliably follow multi-file chains
```

- [ ] **Step 3: Commit planning checkpoint**

```bash
git add docs/superpowers/plans/2026-04-23-workspace-memory-platform-neutral-docs.md
git commit -m "docs: add plan for platform-neutral workspace-memory update"
```

Expected: A commit containing only the plan file.

### Task 2: Update the documentation

**Files:**
- Modify: `README.md`
- Modify: `INSTALL.agent.md`
- Modify: `skills/workspace-memory/SKILL.md`
- Modify: `skills/workspace-memory/references/protocol.md`

- [ ] **Step 1: Edit user-facing docs**

Add or rewrite content so the repository README and installation entrypoint:

```text
- avoid sounding Codex-first
- emphasize capability-based support across runtimes
- tell users to review INSTALL.agent.md before following it
```

- [ ] **Step 2: Edit skill behavior definitions**

Add or rewrite content so the skill and protocol:

```text
- preserve the current lightweight three-file model
- describe optional index/pointer files only for larger workspaces
- require verifying recalled memory against current files, code, or repo state before relying on it
- explain that thin shims should be strong enough to reliably point weaker agents at the canonical file
```

- [ ] **Step 3: Commit documentation update**

```bash
git add README.md INSTALL.agent.md skills/workspace-memory/SKILL.md skills/workspace-memory/references/protocol.md
git commit -m "docs: make workspace-memory guidance platform-neutral"
```

Expected: A commit containing the four documentation changes.

### Task 3: Verify the changes

**Files:**
- Modify: `PROJECT_PROGRESS.md`

- [ ] **Step 1: Verify required phrases and rules exist**

Run: `rg -n "review.*INSTALL\\.agent|verify before recall|index|pointer|AGENTS.md directly|shim" README.md INSTALL.agent.md skills/workspace-memory/SKILL.md skills/workspace-memory/references/protocol.md`
Expected: Matches confirming the new capability-first positioning, installation safety language, optional index/pointer guidance, and verify-before-recall rule.

- [ ] **Step 2: Review the diff**

Run: `git diff -- README.md INSTALL.agent.md skills/workspace-memory/SKILL.md skills/workspace-memory/references/protocol.md docs/superpowers/plans/2026-04-23-workspace-memory-platform-neutral-docs.md`
Expected: Only the intended documentation updates and no unrelated edits.

- [ ] **Step 3: Record project memory if warranted**

If the session materially changed the skill direction, add a top entry to `PROJECT_PROGRESS.md` that records:

```text
- the shift to capability-first wording
- the addition of optional index/pointer guidance
- the new verify-before-recall rule
- the installation safety wording change
```

- [ ] **Step 4: Commit memory update if made**

```bash
git add PROJECT_PROGRESS.md
git commit -m "docs: record workspace-memory documentation direction"
```

Expected: Skip this step if PROJECT_PROGRESS.md was not updated.

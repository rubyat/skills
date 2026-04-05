# Git Commit Slash Command — Interactive Commit with Approval

A slash command for Claude Code that proposes a commit message, waits for your approval, then commits and pushes.

## Setup

Create at **one** of these locations:

**Personal (works everywhere):**
```
~/.claude/commands/commit.md
```

**Project-specific:**
```
.claude/commands/commit.md
```

---

## Command Content

```markdown
---
description: Stage changes, propose a commit message, wait for approval, then commit and push
allowed-tools: Bash(git *)
---

You are handling a git commit workflow. Follow these steps exactly.

## Step 1: Inspect

Run these and review the output:
- `git status`
- `git diff --staged` and `git diff`
- `git log --oneline -10` (to match the repo's commit style)
- `git branch --show-current`

If there's a merge conflict, detached HEAD, or nothing to commit, stop and report.

## Step 2: Stage

If nothing is staged, run `git add -A`. Never stage files that look like secrets (`.env`, `*.key`, `*.pem`, credentials).

## Step 3: Propose a commit message

Write a commit message following Conventional Commits:
- `type(scope): subject` — types: feat, fix, docs, style, refactor, test, chore, perf, build, ci
- Subject under 72 chars, imperative mood
- Add a body explaining *why* if the change is non-trivial
- Match the style from `git log` if the repo uses something different

Present it like this and then **STOP**:

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📝 PROPOSED COMMIT MESSAGE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
<message>
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

Then show: files staged, current branch, push target. Ask:

> Reply with: `approve` / `edit: <message>` / `regenerate` / `cancel`

**Do not run `git commit` or `git push` yet. Wait for my reply.**

## Step 4: Act on my reply

- `approve` → commit with your message, then `git push` (use `-u origin <branch>` if no upstream)
- `edit: <msg>` → commit with my message, then push
- `regenerate` → write a *meaningfully different* message, present again, stop
- `cancel` → leave everything staged, stop

## Safety rules
- Never `git push --force`
- Never commit to `main`/`master` without confirming
- Never run `git reset --hard` or `git clean -fd`
- If push fails due to remote changes, stop and report — don't force
```

---

## Usage

Type `/commit` in Claude Code whenever you want to commit. Claude will:
1. Inspect the working tree
2. Stage appropriate files
3. Propose a commit message
4. Wait for your approval
5. Commit and push on `approve`

---

## Extending Later

If you find yourself wanting the same commit style applied elsewhere (PR descriptions, changelogs), extract the style rules into a skill and have `/commit` reference it.

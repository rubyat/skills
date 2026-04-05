---
description: Generate a conventional commit message from the current staged and unstaged changes
allowed-tools: Bash(git status:*), Bash(git diff:*), Bash(git log:*), Bash(git branch:*)
---

You are generating a commit message proposal. You will NOT stage, commit, or push anything — only read the repo state and propose a message.

## Step 1: Inspect

Run these to understand the changes:
- `git status`
- `git diff --staged`
- `git diff` (unstaged changes, in case nothing is staged yet)
- `git log --oneline -10` to see the commit message style used in this repo
- `git branch --show-current`

If there are no changes at all (staged or unstaged), stop and report that there's nothing to commit.

## Step 2: Write the message

Follow Conventional Commits format:
- `type(scope): subject`
- Types: `feat`, `fix`, `docs`, `style`, `refactor`, `test`, `chore`, `perf`, `build`, `ci`
- Subject under 72 characters, imperative mood ("add" not "added", "fix" not "fixed")
- Add a blank line and a short body explaining *why* if the change is non-trivial
- If the repo's existing commits in `git log` don't use conventional commits, match that style instead

Prefer the staged diff if something is staged; otherwise base the message on the unstaged diff.

## Step 3: Present

Output exactly this format:

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📝 PROPOSED COMMIT MESSAGE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
<message here>
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

Then a one-line summary: which files it covers and the current branch.

Do not run `git add`, `git commit`, or `git push`. Just propose the message and stop.

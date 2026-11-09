# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a **prompts repository** — a collection of AI prompts, Claude Code slash commands, and workflow guides for personal use and open source sharing. It is not a software project: there is nothing to build, lint, test, or run. Do not add build/test/lint commands.

## Repository Structure

- `coding/` — code-related prompts and slash commands (the only populated category so far)
- `writing/`, `analysis/`, `creative/` — planned categories listed in `README.md`; the folders do not exist yet, so create one when the first prompt for it is added
- `superpowers/README.md` — a reference guide to the `superpowers:*` Claude Code skills (when to use each, how they chain). It documents skills that live in a plugin, not in this repo.

## File Formats

Prompts in `coding/` come in two shapes. Match the existing one that fits:

1. **Raw slash command** (e.g. `coding/commit-msg.md`) — the file *is* the command. It starts with YAML frontmatter (`description`, `allowed-tools`) followed by the instructions, so it can be copied directly to `~/.claude/commands/` or `.claude/commands/`.
2. **Documented prompt or command** (e.g. `coding/git-commit-workflow.md`, `coding/project-analysis.md`) — a titled doc with setup and usage notes, with the actual command content embedded in a fenced block, or the prompt written as the document body.

`commit-msg.md` (read-only, proposes a message) and `git-commit-workflow.md` (stages, commits, pushes after approval) cover deliberately different scopes. Keep them distinct rather than merging them.

## Adding or Changing Prompts

- Check existing files first to avoid duplicates; if a prompt fits several categories, pick the most specific one.
- Use descriptive kebab-case filenames (`code-review.md`, `bug-fixing.md`) and action-oriented titles.
- Each prompt must be self-contained, focused, and practical. No generic filler.
- **Update the category list in `README.md`** with a link and a one-line description whenever a prompt is added, renamed, or removed. The README is the index.

## Commit Style

Use Conventional Commits scoped by category, e.g. `docs(coding): add commit-msg slash command`.

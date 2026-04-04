# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a **prompts repository** — a collection of AI prompts organized by category for personal use and open source sharing. It is not a software project to build or run.

## Repository Structure

```
skills/
├── coding/        # Code-related prompts (review, debug, refactor, analysis)
├── writing/       # Writing prompts (emails, docs, copywriting)
├── analysis/      # Thinking/analysis prompts (architecture, data)
└── creative/      # Creative prompts (brainstorming, ideation)
```

## Guidelines for Claude

- When adding prompts, place them in the most relevant category
- Keep prompts focused and practical — avoid generic filler
- Name files descriptively: `bug-fixing.md`, `code-review.md`, etc.
- If a prompt fits multiple categories, pick the most specific one
- When improving prompts, maintain clarity and conciseness
- Do not add build/test/lint commands — this is a prompts collection, not software

## Adding New Prompts

1. Create a new `.md` file in the appropriate category folder
2. Use clear, action-oriented titles
3. Include enough context for the prompt to be useful without additional input
4. Avoid redundant prompts — check existing files first

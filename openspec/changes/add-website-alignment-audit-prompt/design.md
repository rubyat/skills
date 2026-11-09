## Context

This repository is a prompt collection, not software. `coding/` holds three prompts in two formats: raw slash commands with YAML frontmatter (`commit-msg.md`) and documented prompts whose body is the prompt (`project-analysis.md`). `README.md` serves as the index. The user pasted a long, ten-phase website alignment audit prompt and asked for it to be added.

A cleaned copy of that prompt is stored in this change as `source-prompt.md`, so the apply step does not depend on this conversation.

## Goals / Non-Goals

**Goals:**
- Add the prompt as one self-contained file that can be pasted into any website project.
- Keep the user's content and structure faithful to the original.
- Keep the README index in sync.

**Non-Goals:**
- Rewriting, shortening, or restructuring the prompt's phases.
- Converting the prompt into a slash command with frontmatter.
- Creating a new `web/` or `frontend/` category.
- Building tooling, such as Playwright scripts, to accompany the prompt.

## Decisions

- **Category is `coding/`**: The prompt drives code changes (CSS, layout components) and verification. Per CLAUDE.md, choose the most specific category that already exists. A new `frontend/` category for a single file would fragment the index. *Alternative considered:* `analysis/`. Rejected because the prompt explicitly calls for implementation, not just an audit.
- **Format is a documented prompt with the body as the prompt** (like `project-analysis.md`): The prompt is long and framework-agnostic, and users will typically paste it or reference it. *Alternative considered:* a raw slash command with `description` and `allowed-tools` frontmatter. Rejected because the prompt needs browser tooling, which varies by setup (Playwright MCP, Chrome DevTools, or Claude in Chrome), so pinning `allowed-tools` would break portability. A user can still copy the file into `.claude/commands/` and add frontmatter.
- **Filename is `website-alignment-audit.md`**: It is kebab-case, descriptive, and shorter than the full title.
- **Edits are minimal**: Only paste artifacts change. These are `\!important` (written as `!important`) and the trailing "here add this". Headings, lists, and the viewport table stay verbatim.

## Risks / Trade-offs

- [The prompt is long, about 300 lines, compared with the other entries.] → This is acceptable. CLAUDE.md asks for focused and practical prompts, and this one is focused on a single task. Do not trim it, because the user's phases encode their workflow.
- [A user might expect a slash command.] → The README description says it is a prompt. Converting it later is a separate change.

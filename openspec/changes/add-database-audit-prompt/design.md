## Context

This repository is a prompt collection, and `README.md` is its index. The `add-website-alignment-audit-prompt` change set the pattern for adding a long, user-supplied audit prompt: store a cleaned copy as `source-prompt.md` in the change folder, then copy it into `coding/` during apply. This change follows the same pattern.

## Goals / Non-Goals

**Goals:**
- Add the database audit prompt as one self-contained file.
- Keep the user's phases, priorities, and safety rules faithful to the original.
- Keep the README index in sync.

**Non-Goals:**
- Rewriting, shortening, or merging this prompt with the website alignment audit.
- Converting it to a slash command.
- Adding database-specific helper scripts.
- Creating a new `database/` or `security/` category.

## Decisions

- **Category is `coding/`**: The prompt drives code changes such as migrations, ORM queries, and tests, so `coding/` fits. *Alternatives considered:* `analysis/` was rejected because the prompt demands implementation. A new `database/` category was rejected because a single file would fragment the index.
- **Format is a documented prompt with the body as the prompt**: This matches `project-analysis.md` and `website-alignment-audit.md`. The prompt needs engine-specific tools that vary by project (MySQL, PostgreSQL, SQL Server), so pinning `allowed-tools` in slash-command frontmatter would hurt portability.
- **Filename is `database-audit.md`**: It is short and descriptive. The H1 title carries the full scope: performance, queries, relationships, and security.
- **Edits are minimal**: Drop only the leading `/opsx:propose` invocation line. Keep the horizontal rule after the Primary Objective as it appears in the source.

## Risks / Trade-offs

- [The prompt is very long, about 580 lines.] → This is acceptable, because it covers a single coherent task and the length reflects the user's chosen depth. Do not trim it.
- [Users could run destructive operations if they ignore the safety phase.] → Phase 15 is kept verbatim and is prominent in the prompt. No change is needed.

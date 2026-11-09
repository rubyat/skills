## Why

The collection has a front-end layout audit prompt but nothing for the database layer. The user has a detailed sixteen-phase prompt for auditing database performance, queries, relationships, and SQL injection risk, and wants it added so it can be reused across application projects.

## What Changes

- Add `coding/database-audit.md`, a documented prompt that tells an AI agent to do the following:
  - Discover the database stack and measure a performance baseline.
  - Find slow queries, index gaps, join and relationship problems, and N+1 queries.
  - Audit for SQL injection.
  - Implement safe fixes and verify them with before and after measurements.
  - Follow strict production-safety rules throughout.
- Keep all of the user's content unchanged in substance: Phases 1–16, Definition of Done, and the Final Execution Instruction.
- Drop the leading `/opsx:propose` line from the pasted text, because it is an invocation and not part of the prompt.
- Add a link and a one-line description under **Coding** in `README.md`.

## Capabilities

### New Capabilities
- `database-audit-prompt`: A self-contained prompt in the `coding/` category for auditing and optimizing database performance, relationships, and SQL injection security. Includes its README index entry.

### Modified Capabilities
<!-- None. No existing specs in openspec/specs/. -->

## Impact

- New file: `coding/database-audit.md`
- Modified: `README.md` (Coding category list)
- No code, dependencies, or tooling are affected.

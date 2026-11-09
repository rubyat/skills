## Why

The repository has no prompt for front-end layout work. The user has a detailed, phase-based prompt for a project-wide website alignment, container consistency, and responsive layout audit, and wants it in the collection so it can be reused across website projects.

## What Changes

- Add `coding/website-alignment-audit.md`, a documented prompt that tells an AI agent to discover a site's layout system, measure rendered alignment across 10 viewport widths, fix root causes in the shared container system, verify with before and after screenshots, and report results.
- Keep the user's ten phases (Discovery, Alignment Reference, Visual Inspection, Root Cause, Container System, Page Fixes, Responsive, Verification, Production Safety, Final Report), plus the Completion Criteria and Execution Instructions, unchanged in substance.
- Fix paste artifacts in the source text, such as the escaped `\!important`, and give the file a clean, action-oriented title.
- Add a link and a one-line description for the new prompt under **Coding** in `README.md`.

## Capabilities

### New Capabilities
- `website-alignment-audit-prompt`: A self-contained prompt in the `coding/` category for auditing and fixing website container alignment, horizontal spacing, and responsive layout, and its entry in the README index.

### Modified Capabilities
<!-- None. No existing specs in openspec/specs/. -->

## Impact

- New file: `coding/website-alignment-audit.md`
- Modified: `README.md` (Coding category list)
- No code, dependencies, or build tooling are affected, since this is a prompts-only repository.

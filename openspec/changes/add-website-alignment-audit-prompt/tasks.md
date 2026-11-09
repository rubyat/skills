## 1. Add the prompt file

- [x] 1.1 Copy `openspec/changes/add-website-alignment-audit-prompt/source-prompt.md` to `coding/website-alignment-audit.md`
- [x] 1.2 Verify that the H1 title, the Objective, Phase 1 through Phase 10, Completion Criteria, Execution Instructions, and Expected Result all appear in order
- [x] 1.3 Verify that the Phase 3 viewport table lists all 10 widths (1920, 1440, 1366, 1280, 1024, 768, 430, 390, 375, and 320)
- [x] 1.4 Run `grep -nE '\\!|here add this|/opsx' coding/website-alignment-audit.md` and confirm that it returns no matches

## 2. Update the README index

- [x] 2.1 Under `### Coding` in `README.md`, add `- [Website Alignment Audit](coding/website-alignment-audit.md) — Audit and fix container alignment, gutters, and responsive layout across a website`
- [x] 2.2 Confirm that the link resolves and that the entry matches the format of the existing Coding entries

## 3. Wrap up

- [x] 3.1 Run `openspec validate add-website-alignment-audit-prompt` and fix any errors it reports
- [ ] 3.2 Propose the commit message `docs(coding): add website alignment audit prompt`, and commit only after the user approves it

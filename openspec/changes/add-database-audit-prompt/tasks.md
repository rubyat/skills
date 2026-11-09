## 1. Add the prompt file

- [ ] 1.1 Copy `openspec/changes/add-database-audit-prompt/source-prompt.md` to `coding/database-audit.md`
- [ ] 1.2 Verify that the H2 headings appear in order: Primary Objective, Phase 1 through Phase 16, Definition of Done, Final Execution Instruction
- [ ] 1.3 Verify that Phase 13 has all four priority tiers and that Phase 15 keeps every safety rule
- [ ] 1.4 Run `grep -nE '/opsx|now add this|\\!' coding/database-audit.md` and confirm that it returns no matches

## 2. Update the README index

- [ ] 2.1 Under `### Coding` in `README.md`, add `- [Database Audit](coding/database-audit.md) — Audit and optimize slow queries, indexes, joins, N+1 issues, and SQL injection risks`
- [ ] 2.2 Confirm that the link resolves and that the entry matches the existing format

## 3. Wrap up

- [ ] 3.1 Run `openspec validate add-database-audit-prompt` and fix any errors
- [ ] 3.2 Propose the commit message `docs(coding): add database audit prompt`, and commit only after the user approves

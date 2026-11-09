## ADDED Requirements

### Requirement: Prompt file exists in coding category
The repository SHALL contain `coding/database-audit.md`. It SHALL be a documented prompt whose body is the prompt, with a kebab-case filename and an action-oriented H1 title.

#### Scenario: File present with correct title
- **WHEN** a user lists the `coding/` directory
- **THEN** `database-audit.md` is present and its first line is an H1 title naming a database performance, query optimization, relationships, and security audit

### Requirement: Prompt preserves source content
The prompt SHALL keep every section of the user-supplied source in its original order. The sections are the Primary Objective, Phases 1 through 16, Definition of Done, Final Execution Instruction, and the Expected result statement. Phase 13 SHALL keep all four priority tiers, and Phase 15 SHALL keep every production safety rule.

#### Scenario: All phases present
- **WHEN** a reader scans the prompt's H2 headings
- **THEN** Primary Objective, Phase 1 through Phase 16, Definition of Done, and Final Execution Instruction appear in order

#### Scenario: Safety rules intact
- **WHEN** a reader views Phase 15
- **THEN** the rules forbidding production table resets, record deletion, automatic destructive migrations, and secret exposure are all present

### Requirement: Prompt is clean and self-contained
The prompt SHALL contain no invocation lines or paste artifacts, such as `/opsx:propose`, "now add this", or backslash-escaped characters. It SHALL be usable in any project without editing.

#### Scenario: No stray lines
- **WHEN** the file is searched for `/opsx`, `now add this`, or `\!`
- **THEN** no matches are found

### Requirement: README index updated
`README.md` SHALL list the new prompt under **Coding**, with a relative link and a one-line description in the existing `[Title](path) — description` format.

#### Scenario: README entry present
- **WHEN** a reader views the Coding section of `README.md`
- **THEN** an entry links to `coding/database-audit.md` with a one-line description

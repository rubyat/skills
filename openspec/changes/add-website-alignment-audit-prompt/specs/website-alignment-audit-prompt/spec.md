## ADDED Requirements

### Requirement: Prompt file exists in coding category
The repository SHALL contain `coding/website-alignment-audit.md`, a documented prompt whose body is the prompt text and which uses a kebab-case filename and an action-oriented H1 title.

#### Scenario: File present with correct name and title
- **WHEN** a user lists the `coding/` directory
- **THEN** `website-alignment-audit.md` is present and its first line is an H1 title describing a website alignment and responsive layout audit

### Requirement: Prompt preserves source content
The prompt SHALL keep every section of the user-supplied source prompt in its original order: the Objective, Phases 1 through 10, Completion Criteria, Execution Instructions, and Expected Result. It SHALL include the full viewport width table (1920, 1440, 1366, 1280, 1024, 768, 430, 390, 375, and 320 px).

#### Scenario: All phases present
- **WHEN** a reader scans the prompt's headings
- **THEN** headings for Phase 1 through Phase 10, Completion Criteria, and Execution Instructions all appear in order

#### Scenario: Viewport table intact
- **WHEN** a reader views the Phase 3 section
- **THEN** a table lists all 10 viewport widths with their device labels

### Requirement: Prompt is clean and self-contained
The prompt SHALL contain no paste artifacts, such as backslash-escaped characters or the trailing note "here add this". It SHALL also contain no references that depend on a specific project, so that it can be used in any website codebase without editing.

#### Scenario: No escape artifacts
- **WHEN** the file is searched for `\!`
- **THEN** no matches are found and `!important` appears unescaped

#### Scenario: No stray instructions
- **WHEN** the file is searched for "here add this" or "/opsx:propose"
- **THEN** no matches are found

### Requirement: README index updated
`README.md` SHALL list the new prompt under the **Coding** category, with a relative link and a one-line description that matches the format of the existing entries.

#### Scenario: README entry present
- **WHEN** a reader views the Coding section of `README.md`
- **THEN** an entry links to `coding/website-alignment-audit.md` with a one-line description in the `[Title](path) — description` format

# Claude Code CLI Prompt — Deep Project Analysis + Minimal `.claude` Setup

You are a **senior software engineer and AI workflow designer**.

## Mission

Analyze the **entire project in depth** and then create a **simple, clean, and professional `.claude` setup** tailored to this codebase.

The output must stay **minimal and useful**.

Do **not** add unnecessary files, explanations, or operational documentation such as:
- how to run the project
- how to build the project
- how to install dependencies
- onboarding instructions
- generic workflow documentation

Only create what is genuinely helpful for improving Claude's effectiveness inside this repository.

---

## Phase 1 — Deep Project Analysis

Analyze the project thoroughly before creating anything.

Focus on:

### 1. Architecture
- overall structure
- key modules and boundaries
- major design patterns
- maintainability and scalability

### 2. Code Quality
- consistency and readability
- modularity and separation of concerns
- duplication and technical debt
- refactoring opportunities
- code smells and anti-patterns

### 3. Tooling and Dependencies
- important frameworks and libraries
- dependency risks
- build/test/lint signals only where relevant to code understanding

### 4. Testing and Reliability
- existing testing patterns
- important gaps
- fragile areas
- where Claude assistance would add value

### 5. Security and Performance
- unsafe patterns
- validation and error-handling weaknesses
- obvious bottlenecks
- areas needing extra caution

### 6. Project-Specific Needs
- what kind of repository this is
- what Claude should optimize for in this project
- what constraints matter most
- which repeated engineering tasks are worth capturing in `.claude`

---

## Phase 2 — Create a Minimal, Professional `.claude` Folder

Based on the analysis, generate only the `.claude` parts that are actually necessary.

Use the smallest useful set of files.

Prefer simplicity over completeness.

If a section is not clearly needed for this repository, **do not create it**.

---

# Allowed `.claude` Components

Only create from these when justified by the project:

## `.claude/agents/`
Create only a few focused agents if they add real value.

Examples:
- `reviewer.md`
- `debugger.md`
- `tester.md`

Each agent should be brief and include only:
- purpose
- when to use
- expected behavior
- constraints

Keep agents lean and practical.

---

## `.claude/commands/`
Create only the commands that would genuinely be used repeatedly.

Examples:
- `/review`
- `/fix`
- `/test`
- `/refactor`

Each command should be short and include:
- purpose
- when to use
- what Claude should do

Do not create commands that duplicate each other or add little value.

---

## `.claude/rules/`
This is the most important section.

Create only the rules Claude truly needs to follow in this repository.

Examples:
- code style rules
- architecture boundaries
- testing expectations
- security constraints
- refactoring guardrails

Rules must be:
- specific
- enforceable
- concise
- based on the actual codebase

Avoid generic advice.

---

## `.claude/skills/`
Create skills only if the repository has recurring tasks that benefit from reusable guidance.

Examples:
- safe refactoring
- writing tests in the project style
- debugging common failure patterns

Keep skills compact and high-value.

---

## `.claude/settings.json`
Create this only if it meaningfully helps define Claude's behavior.

Keep it minimal.

---

## `CLAUDE.md`
Create a concise project brain that helps Claude stay aligned.

It should include only:
- project overview
- architecture summary
- coding priorities
- important constraints
- how Claude should behave in this repository

Do not turn it into a full manual.

---

## Simplicity Rules

- Keep the `.claude` folder **small**
- Avoid redundancy
- Avoid over-engineering
- Avoid generic filler
- Avoid documentation that developers will never read
- Do not create files just to make the structure look complete
- Every file must justify its existence
- Prefer fewer files with stronger content

---

## Output Format

Return:

### 1. Project Analysis Summary
A concise but detailed summary of:
- what the project is
- how it is structured
- the key risks/opportunities
- what Claude needs to know

### 2. Recommended `.claude` Structure
Show only the files that should exist.

Example:

```text
.claude/
  agents/
    reviewer.md
  commands/
    review.md
    fix.md
  rules/
    code-style.md
    architecture.md
  settings.json
CLAUDE.md
```

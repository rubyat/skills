# Superpowers

Structured workflows that turn chaotic development into systematic progress. Each superpower is a proven path for a specific situation.

**Invoke with:** `/superpowers:<name>` or the `Skill` tool

---

## Quick Decision Guide

**What are you trying to do?**

| I'm starting something new | → [`brainstorming`](#brainstorming) |
| I have a bug to fix | → [`systematic-debugging`](#systematic-debugging) |
| I need a plan | → [`writing-plans`](#writing-plans) |
| I'm ready to build | → [`subagent-driven-development`](#subagent-driven-development) or [`executing-plans`](#executing-plans) |
| I'm done and need to wrap up | → [`verification-before-completion`](#verification-before-completion) |
| I need to isolate work | → [`using-git-worktrees`](#using-git-worktrees) |
| I have multiple independent problems | → [`dispatching-parallel-agents`](#dispatching-parallel-agents) |
| I want someone to review my code | → [`requesting-code-review`](#requesting-code-review) |
| I received feedback on my code | → [`receiving-code-review`](#receiving-code-review) |
| I finished a feature, what's next? | → [`finishing-a-development-branch`](#finishing-a-development-branch) |
| I need to write a new skill | → [`writing-skills`](#writing-skills) |

---

## The Full Workflow

For major features, superpowers chain together:

```
brainstorming → writing-plans → subagent-driven-development → verification-before-completion → requesting-code-review
                 (or executing-plans)
```

Each step is required before moving to the next. This isn't bureaucratic overhead — it's how you avoid the "oops" moments.

---

## brainstorming

**Use when:** Building anything new — features, components, or modifying behavior.

**Don't start coding until you have a approved design.**

### The Flow
1. Explore project context
2. Ask questions (one at a time)
3. Propose 2-3 approaches with trade-offs
4. Present design sections → get approval after each
5. Write design doc → commit to git
6. Invoke `writing-plans` to create implementation plan

### Real-Life Example

```
You: /superpowers brainstorming
AI: "I'm using brainstorming to explore your idea. Let me first understand the project context..."

[Explores codebase]
AI: "I see this is a user auth system. Before diving in — will this feature involve UI mockups?"
You: "Yes, it's a login flow redesign"
AI: "Some of what we're working on might be easier to explain in a web browser. Want to try it?"

[You agree]
AI: [Shows mockup options visually]

AI: "Let's start with the basics. What's the primary goal of the new login flow?"

You: [Answer question]
AI: "Got it. Next question: should social login be part of this flow or separate?"

... [continues with focused questions]

AI: "Here are 3 approaches I recommend:
    A. Single-page modal (simpler, faster)
    B. Multi-step wizard (better for complex flows)
    C. Redirect to hosted auth (most secure)

    I recommend A — faster implementation, covers 90% of use cases..."

[You approve design sections]
AI: "Design complete. Writing spec to docs/superpowers/specs/2026-04-15-login-redesign.md"
AI: "Spec committed. Invoking writing-plans to create the implementation plan..."
```

### Key Principles
- **Even "simple" projects need design** — a todo list is a project
- **One question at a time** — don't overwhelm
- **Multiple choice preferred** — easier to answer
- **YAGNI ruthlessly** — cut unnecessary features
- **Design for isolation** — small units with clear boundaries

---

## systematic-debugging

**Use when:** Any bug, test failure, unexpected behavior, or when something isn't working.

**Iron Law:** NO FIXES WITHOUT ROOT CAUSE INVESTIGATION FIRST

### The Four Phases

```
Phase 1: Root Cause     → Read errors, reproduce, check recent changes, gather evidence
Phase 2: Pattern       → Find working examples, compare against broken code
Phase 3: Hypothesis    → Form theory, test minimally
Phase 4: Implementation → Create failing test, fix root cause, verify
```

### Stop and Ask When...

| If You Catch Yourself Thinking | Reality |
|--------------------------------|---------|
| "Quick fix for now" | That's rationalization |
| "Let me try X and see if it works" | Guessing, not debugging |
| "I'll just increase the timeout" | Masking the symptom |
| "One more fix attempt" (after 2+ failures) | 3+ failures = architectural problem |
| "I see the problem" | Seeing symptoms ≠ understanding root cause |

### Real-Life Example

```
You: /superpowers systematic-debugging
AI: "I'm using systematic-debugging. Tell me about the bug."

You: "The login button doesn't work on iOS Safari"

AI: "Phase 1: Root Cause Investigation. Let me start by reading the error messages carefully.

    What happens when you click the button? Does it:
    a) Do nothing
    b) Show an error
    c) Navigate to wrong page
    d) Something else"

You: "It does nothing - no error, no navigation"

AI: "Can you reproduce it consistently? What are the exact steps?"

You: [Steps to reproduce]
AI: "Has anything changed recently? New deployments, config changes, dependency updates?"

You: "We just updated to iOS 17.4"

AI: "iOS 17.4 — let me check for Safari compatibility changes...
    [Finds WebKit changes affecting touch handlers]

    Phase 2: Pattern Analysis. Let me find working examples in the codebase..."

[Continues through phases until root cause found]

AI: "Root cause identified: iOS 17.4 changed touch event delegation behavior.
    Phase 4: Creating failing test, then implementing fix..."

AI: "Fix verified — login button works on iOS 17.4 Safari. Test added to prevent regression."
```

### The Red Flag Rule

**If 3+ fixes have failed:** STOP. Question the architecture. Fixing symptoms in different places = wrong pattern, not bad luck.

---

## writing-plans

**Use when:** You have an approved design/spec and need a detailed implementation roadmap.

### The Output

Each plan is:
- **Bite-sized tasks** (2-5 minute steps)
- **Exact file paths** always
- **Complete code** in every step
- **Run commands** with expected output
- **TDD-first** — tests before implementation

### Plan Document Structure

```markdown
# [Feature Name] Implementation Plan

**Goal:** [One sentence]

**Architecture:** [2-3 sentences]

**Tech Stack:** [Key technologies]

---

### Task 1: [Component Name]

**Files:**
- Create: `exact/path/to/file.py`
- Modify: `exact/path/to/existing.py:123-145`

- [ ] **Step 1: Write failing test**
- [ ] **Step 2: Run test, verify it fails**
- [ ] **Step 3: Write minimal implementation**
- [ ] **Step 4: Run test, verify it passes**
- [ ] **Step 5: Commit**
```

### No Placeholders Rule

Every step contains actual content. These are **plan failures:**
- "TBD", "TODO", "implement later"
- "Add appropriate error handling"
- "Write tests for the above" (without code)
- "Similar to Task N"

### Real-Life Example

```
AI: "Writing plan for login flow implementation...

    Task 1: LoginModal Component
    Files: Create: src/components/LoginModal.tsx

    - [ ] Step 1: Write failing test for modal visibility toggle
    - [ ] Step 2: Run test, verify FAIL (component not found)
    - [ ] Step 3: Write minimal Modal with isOpen prop
    - [ ] Step 4: Run test, verify PASS
    - [ ] Step 5: Commit "feat: add LoginModal with visibility toggle"

    Task 2: Email validation
    ...

Plan complete (5 tasks). Two execution options:

1. Subagent-Driven (recommended) — I dispatch fresh agent per task
2. Inline Execution — Execute tasks here with checkpoints

Which approach?"
```

---

## executing-plans

**Use when:** You have a written plan and want to execute it step-by-step in a separate session.

### When to Use vs. subagent-driven-development

| Same session, want review between tasks | → subagent-driven-development |
| Separate session, batch execution | → executing-plans |
| Want subagent per task | → subagent-driven-development |

### The Process

```
1. Load and review plan (critically)
2. Execute each task:
   - Mark in_progress
   - Follow each step exactly
   - Run verifications
   - Mark complete
3. After all tasks: Invoke finishing-a-development-branch
```

### When to Stop and Ask

- Hit a blocker (missing dependency, unclear instruction)
- Plan has critical gaps
- Verification fails repeatedly
- Don't understand an instruction

**Ask for clarification rather than guessing.**

---

## subagent-driven-development

**Use when:** You have a plan and want to execute it with fresh subagents, one per task, in the current session.

**Recommended for most implementations.**

### Why Subagents?

- Fresh context per task (no confusion)
- Parallel-safe (subagents don't interfere)
- Two-stage review after each task: spec compliance, then code quality
- Faster iteration

### The Process

```
Read plan → Extract tasks → Create TodoWrite

For each task:
  1. Dispatch implementer subagent
  2. Subagent asks questions (if any)
  3. Subagent implements, tests, commits, self-reviews
  4. Dispatch spec compliance reviewer
  5. If issues → implementer fixes → review again
  6. Dispatch code quality reviewer
  7. If issues → implementer fixes → review again
  8. Mark task complete

After all tasks → finishing-a-development-branch
```

### Real-Life Example

```
You: /superpowers subagent-driven-development

AI: "Reading plan file... Extracting 5 tasks...

  Task 1: Hook installation script
  Task 2: Recovery modes
  Task 3: Progress reporting
  Task 4: Config validation
  Task 5: Documentation

Dispatching Task 1 implementer..."

Implementer: "Before I begin — should the hook be user or system level?"
You: "User level (~/.config/superpowers/hooks/)"

[Implementer completes Task 1, commits]

AI: "Dispatching spec compliance reviewer..."
Spec reviewer: ✅ Spec compliant

AI: "Dispatching code quality reviewer..."
Code reviewer: ✅ Approved

[Task 1 marked complete, Task 2 begins...]

[After all 5 tasks complete]
AI: "All tasks complete. Invoking finishing-a-development-branch..."
```

---

## verification-before-completion

**Use when:** About to claim work is complete, fixed, or passing — before committing or creating PRs.

**Iron Law:** NO COMPLETION CLAIMS WITHOUT FRESH VERIFICATION EVIDENCE

### The Gate Function

```
BEFORE claiming any status:

1. IDENTIFY: What command proves this?
2. RUN: Fresh, complete command
3. READ: Full output, check exit code
4. VERIFY: Does output confirm the claim?
   - NO → State actual status with evidence
   - YES → State claim WITH evidence
5. ONLY THEN: Make the claim
```

### Common Failures

| Claim | Requires | Not Sufficient |
|-------|----------|----------------|
| Tests pass | `npm test` output: 0 failures | "They passed before" |
| Build succeeds | Build command: exit 0 | "Logs look good" |
| Bug fixed | Original symptom: now works | "Code changed" |
| Linter clean | Linter output: 0 errors | "Looks fine" |

### Red Flags

Stop if you catch yourself about to say:
- "Should work now"
- "Probably fine"
- "Just this once"
- "Looks correct"
- "I'm confident"
- **Any variation of success without verification**

---

## using-git-worktrees

**Use when:** Starting feature work that needs isolation from current workspace.

### Why Worktrees?

Git worktrees create isolated workspaces sharing the same repository:
- Work on multiple branches simultaneously
- No context switching with `git checkout`
- Clean separation between features

### The Process

```
1. Check for .worktrees/ or worktrees/ directory
2. Verify directory is gitignored
3. Create worktree with new branch
4. Run project setup (npm install, etc.)
5. Verify clean baseline (run tests)
6. Report: "Worktree ready at <path>, tests passing"
```

### Directory Priority

1. `.worktrees/` (preferred, hidden)
2. `worktrees/` (alternative)
3. `~/.config/superpowers/worktrees/<project>/` (global)
4. Ask user

### Safety Rule

**Always verify directory is gitignored** before creating worktree. Prevents accidentally committing worktree contents.

---

## dispatching-parallel-agents

**Use when:** 2+ independent problems that can be investigated without shared context.

### When to Use

```
Multiple failures?
  Are they independent? → Yes → Can they run in parallel? → Yes → USE THIS
                     ↓ No
               Single agent investigates all
```

### Good Fit
- 3+ test files failing with different root causes
- Multiple subsystems broken independently
- Each problem understood without context from others

### Not Good Fit
- Failures are related (fix one might fix others)
- Need to understand full system state
- Exploratory debugging (don't know what's broken yet)

### Real-Life Example

```
You: /superpowers dispatching-parallel-agents

AI: "I see 6 test failures across 3 files:
  - agent-tool-abort.test.ts: 3 failures
  - batch-completion-behavior.test.ts: 2 failures
  - tool-approval-race-conditions.test.ts: 1 failure

Are these independent problem domains?"

You: "Yes, different subsystems"

AI: "Dispatching 3 agents in parallel..."

[Agent 1] Fixes agent-tool-abort.test.ts
[Agent 2] Fixes batch-completion-behavior.test.ts
[Agent 3] Fixes tool-approval-race-conditions.test.ts

[All complete]
AI: "Reviewing summaries... No conflicts detected.
     Running full test suite..."
     
All 6 tests now pass.
```

---

## requesting-code-review

**Use when:** Completing a task, finishing a major feature, or before merging — you want someone to review your code.

### When to Request

**Mandatory:**
- After each task in subagent-driven development
- After completing major feature
- Before merge to main

**Optional but valuable:**
- When stuck (fresh perspective)
- Before refactoring (baseline)
- After fixing complex bug

### The Process

```
1. Get git SHAs (BASE_SHA, HEAD_SHA)
2. Dispatch code-reviewer subagent with crafted context
3. Act on feedback:
   - Critical → Fix immediately
   - Important → Fix before proceeding
   - Minor → Note for later
   - Wrong → Push back with reasoning
```

### Red Flags

**Never:**
- Skip review because "it's simple"
- Ignore Critical issues
- Proceed with unfixed Important issues

**If reviewer is wrong:**
- Push back with technical reasoning
- Show tests that prove it works
- Request clarification

---

## receiving-code-review

**Use when:** You received code review feedback and need to respond/implement it.

### The Response Pattern

```
1. READ: Complete feedback without reacting
2. UNDERSTAND: Restate requirement in own words
3. VERIFY: Check against codebase reality
4. EVALUATE: Technically sound for THIS codebase?
5. RESPOND: Technical acknowledgment or reasoned pushback
6. IMPLEMENT: One item at a time, test each
```

### Forbidden Responses

**NEVER:**
- "You're absolutely right!" (performative)
- "Great point!" / "Excellent feedback!"
- "Let me implement that now" (before verification)

**INSTEAD:**
- Restate the technical requirement
- Ask clarifying questions
- Push back with reasoning if wrong
- Just fix it (actions > words)

### Handling Unclear Feedback

```
IF any item is unclear:
  STOP — do not implement yet
  ASK for clarification

Why: Items may be related. Partial understanding = wrong implementation.
```

### When to Push Back

- Suggestion breaks existing functionality
- Reviewer lacks full context
- Violates YAGNI (unused feature)
- Technically incorrect for this stack
- Conflicts with architectural decisions

---

## finishing-a-development-branch

**Use when:** Implementation is complete, tests pass, and you need to decide what to do next.

### The Process

```
1. Verify tests pass
2. Determine base branch
3. Present 4 options:
4. Execute choice
5. Cleanup worktree
```

### The 4 Options

```
Implementation complete. What would you like to do?

1. Merge back to <base-branch> locally
2. Push and create a Pull Request
3. Keep the branch as-is (I'll handle it later)
4. Discard this work

Which option?
```

### Important Rules

| Option | Action |
|--------|--------|
| 1. Merge locally | Tests pass → merge → cleanup |
| 2. Create PR | Push → PR → keep worktree |
| 3. Keep as-is | Report location → keep worktree |
| 4. Discard | **Confirm first** ("type 'discard' to confirm") |

---

## writing-skills

**Use when:** Creating a new skill, editing an existing one, or verifying skills work.

### When to Write a Skill

- Common pattern in your workflow
- Repetitive process others could reuse
- Best practice you want enforced
- Custom workflow not covered by existing skills

---

## Key Principles

### User Instructions First
User's explicit instructions (CLAUDE.md, direct requests) always override skill behavior.

### Process Skills Before Implementation
- brainstorming, debugging → determine HOW to approach
- Then implementation skills → execute

### No Shortcuts
- Design before code
- Root cause before fixes
- Test before implementation
- Verification before claims

### Rigid vs. Flexible
| Rigid (follow exactly) | Flexible (adapt to context) |
|------------------------|----------------------------|
| TDD | Brainstorming |
| Systematic Debugging | Frontend Design |
| Verification | |
| Code Review | |

---

## Workflow Chains

### New Feature (Full)
```
brainstorming → writing-plans → subagent-driven-development → verification-before-completion → requesting-code-review → finishing-a-development-branch
```

### Bug Fix
```
systematic-debugging → writing-plans → subagent-driven-development → verification-before-completion → finishing-a-development-branch
```

### Quick Fix
```
systematic-debugging → verification-before-completion → finishing-a-development-branch
```

### Parallel Investigation
```
dispatching-parallel-agents → verification-before-completion → finishing-a-development-branch
```

---
name: plan-to-ticket
description: Convert a feature idea, requirement, implementation plan, bug-fix plan, refactor plan, or project change into a concise implementation plan and small, dependency-ordered engineering tickets for Codex or another coding agent. Use when the user asks to break work into tickets, tasks, milestones, implementation steps, or a Plan-to-Ticket workflow. Output text only and do not implement code.
---

# Plan to Ticket

Convert the requested change into a compact implementation plan and small, execution-ready tickets.

## Rules

- Output text only.
- Do not implement code.
- Do not call tools unless repository context is explicitly available and needed.
- Keep tickets small, focused, independently understandable, and independently verifiable.
- Prefer one primary goal per ticket.
- Order tickets by real implementation dependency.
- Do not create artificial dependencies.
- Avoid unrelated refactors, dependency upgrades, formatting changes, or future features.
- If repository context exists, respect its architecture, conventions, constraints, and current state.
- If exact commands or implementation details are unknown, describe verification behavior instead of inventing details.

## Planning Process

Before writing the output, determine internally:

1. The final desired outcome.
2. The minimum foundations required first.
3. The major implementation milestones.
4. Which work can be completed independently.
5. The dependency order between tickets.
6. The scope boundaries that prevent drift.
7. How each ticket can be verified.

Do not expose internal reasoning.

## Ticket Sizing

Prefer tickets that an AI coding agent can complete in one focused pass.

Split a ticket when it contains multiple independent behaviors, unrelated components, or more than one meaningful verification target.

Prefer this:

T0001 - Create user data model
T0002 - Implement authentication service
T0003 - Add login API
T0004 - Add login UI
T0005 - Add route protection

Avoid this:

T0001 - Build authentication, dashboard, permissions, and user management

## Output Format

Always use this structure.

# Plan

1. <Milestone>
2. <Milestone>
3. <Milestone>

# Tickets

### T0001 - <Short title>

**Goal**

<One concrete outcome.>

**Dependencies**

- None

**Scope**

- <What may be changed>
- <Relevant components or behavior>

**Do not touch**

- <Unrelated areas>
- <Future-ticket functionality>

**Requirements**

- <Concrete requirement>
- <Important behavior or edge case>

**Non-goals**

- <Explicitly excluded work>

**Acceptance Criteria**

- <Observable result>
- <Observable result>

**Verification**

- <Automated test, build, API/CLI check, or manual verification>
- <Expected result>

---

Repeat for T0002, T0003, and later tickets.

## Acceptance Criteria

Write observable outcomes, not vague quality statements.

Prefer:

- `POST /api/login` returns HTTP 200 for valid credentials.
- Invalid credentials return HTTP 401.
- Existing authenticated routes continue to work.

Avoid:

- Works correctly.
- Code is clean.
- Feature is complete.

## Existing Repository Context

When repository context is available:

- Read and respect `AGENTS.md` if present.
- Read `docs/Repo_Current_State.md` if present.
- Read architecture or design documentation when directly relevant.
- Treat repository documentation as guidance, but verify important details against actual code when needed.
- Reuse existing patterns before proposing new abstractions or dependencies.

Do not require these files to exist. Keep tickets implementation-neutral when repository context is unavailable.

## Final Output Constraint

Return only the Plan and Tickets sections. Do not add commentary, explanations, code, or implementation after the tickets.

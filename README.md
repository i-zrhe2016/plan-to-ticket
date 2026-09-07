# Plan to Ticket

Plan to Ticket is a Codex skill that turns a feature idea, requirement, bug-fix plan, refactor plan, or other project change into a concise implementation plan and small, dependency-ordered engineering tickets.

The repository contains the skill instructions and its display metadata. It does not contain an application runtime, API, database, or deployment service.

## Architecture

![Plan-to-Ticket logical architecture](docs/diagrams/plan-to-ticket-architecture.svg)

The diagram source is available at [docs/diagrams/plan-to-ticket-architecture.puml](docs/diagrams/plan-to-ticket-architecture.puml). The full explanation is in [docs/architecture/overview.md](docs/architecture/overview.md).

## What it does

When the skill is selected for a planning request, it:

1. Identifies the desired outcome and the minimum implementation foundations.
2. Splits the work into focused, dependency-ordered tickets.
3. Defines scope boundaries, acceptance criteria, and verification for each ticket.
4. Returns text using the `Plan` and `Tickets` sections defined by the skill contract.

The skill is intentionally implementation-neutral. It uses repository context when available, but it does not implement code, add dependencies, or invent commands for unknown tooling.

## Usage

Make the skill available in a Codex skills environment, then provide a change request or implementation idea. The frontmatter description in `SKILL.md` is used for skill selection. The response should contain only a plan and execution-ready tickets.

For repository-aware planning, include the relevant repository in the working context. The skill will reuse existing architecture and conventions where they are documented and available.

## Repository layout

```text
.
├── SKILL.md                              # Skill behavior, workflow, and output contract
├── agents/
│   └── openai.yaml                       # Display metadata for the skill interface
├── docs/
│   ├── architecture/
│   │   └── overview.md                   # Logical architecture and maintenance boundaries
│   └── diagrams/
│       ├── plan-to-ticket-architecture.puml
│       └── plan-to-ticket-architecture.svg
└── README.md                             # Project overview and documentation index
```

## Documentation

- [Architecture overview](docs/architecture/overview.md)
- [Architecture diagram source](docs/diagrams/plan-to-ticket-architecture.puml)
- [Rendered architecture diagram](docs/diagrams/plan-to-ticket-architecture.svg)

## Maintenance

Keep changes scoped to the skill's planning behavior or its supporting documentation. When the output contract changes, update `SKILL.md` and the architecture documentation together. Keep `agents/openai.yaml` limited to interface metadata rather than behavior.

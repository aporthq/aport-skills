# APort Skills

This repo contains workflow skills for AI agents with APort passports.

## Structure

Each directory is a standalone skill with a single `SKILL.md` file:

- `aport-id/` — Register and get a passport
- `aport-complete/` — Verify task completion against deliverable contract
- `aport-standup/` — Generate standup from signed decisions
- `aport-handoff/` — Package verified work for handoff
- `aport-status/` — Show passport, capabilities, recent activity

## Usage

Skills are invoked as slash commands: `/aport-id`, `/aport-complete`, etc.

Each SKILL.md contains the full instructions the agent needs — API endpoints,
request/response shapes, and step-by-step workflow.

## Key concepts

- **Passport**: DID credential issued by APort, carries identity + capabilities + deliverable contract
- **Deliverable contract**: What the agent must deliver — acceptance criteria, summary requirements, test requirements
- **Decision**: Result of a verify call — ALLOW or DENY with reason codes and cryptographic signature
- **Policy pack**: Server-side rules evaluated against the agent's context (e.g. `deliverable.task.complete.v1`)

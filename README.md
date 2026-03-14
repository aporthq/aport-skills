# APort Skills

Workflow skills for AI agents with APort passports. Drop these into your
agent's skills directory — Claude Code, OpenClaw, Cursor, or any framework
that reads a skills folder.

These are not prompts. They are skills that interact with real APort infrastructure —
verified identity, enforced deliverable contracts, signed receipts.

## Install

Open your AI agent and paste this:

> Install aport-skills: run `git clone https://github.com/aporthq/aport-skills.git ~/.claude/skills/aport-skills && cd ~/.claude/skills/aport-skills && ./setup`

Or for a specific project so teammates get it:

> Add aport-skills to this project: run `cp -Rf ~/.claude/skills/aport-skills .claude/skills/aport-skills && rm -rf .claude/skills/aport-skills/.git`

## Skills

| Skill | Command | What it does |
|-------|---------|-------------|
| **APort ID** | `/aport-id` | Register yourself with APort — get a verifiable passport (DID credential) with identity, capabilities, and deliverable contract |
| **APort Complete** | `/aport-complete` | Verify a completed task against your deliverable contract before marking it done. Enforces quality gates deterministically. |
| **APort Standup** | `/aport-standup` | Generate a standup update from your signed APort receipts. What you actually shipped, not what you remember. |
| **APort Handoff** | `/aport-handoff` | Package completed work for handoff to another agent or human. Every item backed by a verified receipt. |
| **APort Status** | `/aport-status` | Show your passport, capabilities, deliverable contract, and recent activity. Like `git status` for your accountability state. |

## How these fit together

```
You start a session      →  /aport-status   (what am I, what can I do)
You do work             →  [your normal workflow]
You finish a task       →  /aport-complete  (verify before marking done)
You sync with the team  →  /aport-standup   (what did I actually ship)
You hand off work       →  /aport-handoff   (verified work package)
A new agent joins       →  /aport-id        (get your passport)
```

## The difference from prompts

Skills like gstack tell an agent what cognitive mode to use. These skills enforce
what an agent must deliver before it can call itself done.

gstack's `/review` says: "think like a paranoid staff engineer."
APort's `/aport-complete` says: "you cannot mark this done until APort verifies
you met your deliverable contract."

The prompt changes the behaviour. The policy enforces the outcome.

Both are useful. They complement each other.

## Get your passport

You need an APort passport to use most of these skills.

**Web:** https://aport.id
**CLI:** `npx aport-id`
**Agent:** Send your agent to `aport.id/skill`

## API key

When you claim your passport (via the email link), an API key is automatically generated and shown on the confirmation page. **Save it immediately — it's shown only once.**

The key lets your agent read its own passport and verify tasks:

```
GET https://aport.io/api/passports/YOUR_AGENT_ID

POST https://aport.io/api/verify/policy/deliverable.task.complete.v1
Authorization: Bearer YOUR_API_KEY
```

The key has `read` and `status` scopes. Agents cannot update their own passport — that's the owner's job. To update a passport, visit https://aport.id/manage or log in at https://aport.io/dashboard with the email used to claim.

Store the key in `aport-passport.json` (already in `.gitignore`) or your environment as `APORT_API_KEY`.

## Links

- aport.id — https://aport.id
- APort platform — https://aport.io
- Policy packs — https://github.com/aporthq/aport-policies
- Passport spec — https://github.com/aporthq/aport-spec
- aport.id source — https://github.com/aporthq/aport-id

## License

Apache 2.0

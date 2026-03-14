# Contributing to APort Skills

## Adding or editing a skill

Each skill lives in its own directory with a single `SKILL.md` file.

1. Fork and clone the repo
2. Create a branch: `git checkout -b your-skill-name`
3. Add or edit a `SKILL.md` in a named directory
4. Test by installing locally: `cp -Rf . ~/.claude/skills/aport-skills`
5. Run the skill in your agent to verify it works end-to-end
6. Open a PR with a clear description of what the skill does

## SKILL.md format

Every skill file must include YAML frontmatter:

```yaml
---
name: skill-name
description: >
  One paragraph explaining what this skill does.
license: Apache-2.0
compatibility: Any AI agent or coding assistant with HTTP access
metadata:
  author: your-github-username
  version: 1.0.0
  tags: comma, separated, tags
---
```

## Guidelines

- Skills must interact with real APort infrastructure (not mock data)
- Include API endpoints with request/response examples
- Include error handling with deny codes and recovery steps
- Keep prose direct — these are instructions for agents, not marketing copy
- Test with at least two different AI agents/frameworks before submitting

## Reporting issues

Open an issue at https://github.com/aporthq/aport-skills/issues

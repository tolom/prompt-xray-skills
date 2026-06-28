# Router Skill

The repository now includes a root `SKILL.md`.

This file works as a router for the whole Prompt X-Ray skill pack.

## What it does

The router selects the right internal workflow for the task:

- vague prompt idea -> `01-prompt-brief-builder`
- existing prompt review -> `02-prompt-auditor`
- assistant system prompt -> `03-system-prompt-architect`
- coding agent instructions -> `04-agent-instruction-writer`
- RAG assistant policy -> `05-rag-answer-policy`
- structured output -> `06-structured-output-designer`
- prompt checks -> `07-prompt-test-generator`
- prompt debugging -> `08-prompt-debugger`
- AI idea to product spec -> `09-prompt-to-product-spec`

## How to use it

Use the root `SKILL.md` when you want one entry point for the whole skill pack.

Use individual folders from `skills/` when you want narrow, task-specific activation.

## Recommended installation styles

### Router style

Place the whole repository inside your tool's skills or project-instructions area.

The important files are:

```text
SKILL.md
skills/
examples/
docs/
```

Then ask for the router explicitly:

```text
Use prompt-xray-skills to audit this prompt.
```

### Individual style

Place only selected folders from `skills/` into your tool's skills or instructions area.

Recommended starter set:

```text
01-prompt-brief-builder
02-prompt-auditor
07-prompt-test-generator
```

## Tool-specific note

- Claude Code can use skill folders directly.
- Codex usually works better through `AGENTS.md` guidance.
- Cursor usually works better through `.cursor/rules`.
- ChatGPT Projects can use selected `SKILL.md` files as project files or instructions.

For detailed setup, see `docs/installation.md`.

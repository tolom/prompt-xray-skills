# Installation and Usage Guide

This repository contains reusable `SKILL.md` workflows.

Different AI tools support reusable instructions differently. Claude Code can use skill folders directly. Codex and Cursor use repository instruction files or rules instead of the same `SKILL.md` skill mechanism.

## Quick recommendation

Use this mapping:

| Tool | Best way to use this repo |
|---|---|
| Claude Code | Copy skill folders into `~/.claude/skills/` or `.claude/skills/` |
| Claude.ai / Claude app | Upload or paste the relevant skill files into a Project/Skill workflow if available |
| Codex | Use `AGENTS.md` and paste references to the relevant skills |
| Cursor | Convert skills into `.cursor/rules/*.mdc` project rules |
| ChatGPT Projects | Add selected `SKILL.md` files as project files/instructions |
| Other agents | Paste the relevant `SKILL.md` into the agent context or project instructions |

## Claude Code

Claude Code supports local skill folders containing `SKILL.md`.

### Global installation

Use this when you want the skills available across projects.

```bash
git clone https://github.com/tolom/prompt-xray-skills.git
mkdir -p ~/.claude/skills
cp -r prompt-xray-skills/skills/* ~/.claude/skills/
```

Then open Claude Code and use one of the trigger phrases:

```text
Audit this prompt using prompt-auditor.
Create a prompt brief for this assistant idea.
Design a system prompt for this support bot.
Write AGENTS.md instructions for this repo.
Create a RAG answer policy.
Generate prompt quality-check cases.
```

### Project-level installation

Use this when you want the skills version-controlled inside a project.

```bash
mkdir -p .claude/skills
cp -r path/to/prompt-xray-skills/skills/* .claude/skills/
```

Recommended for teams:

```text
project/
  .claude/
    skills/
      01-prompt-brief-builder/
        SKILL.md
      02-prompt-auditor/
        SKILL.md
```

### Installing only one skill

Example:

```bash
mkdir -p ~/.claude/skills/prompt-auditor
cp prompt-xray-skills/skills/02-prompt-auditor/SKILL.md ~/.claude/skills/prompt-auditor/SKILL.md
```

Then use:

```text
Use prompt-auditor to audit this prompt:
<prompt>
```

## Claude.ai / Claude app

Depending on the available Claude interface, use one of these approaches:

1. Create a custom skill/project if the interface supports Skills.
2. Upload the relevant skill folder or paste the `SKILL.md` into the project instructions.
3. Add examples from `examples/` as supporting files.
4. Ask Claude to use the named skill workflow.

Suggested first setup:

```text
Add these project files:
- skills/01-prompt-brief-builder/SKILL.md
- skills/02-prompt-auditor/SKILL.md
- skills/07-prompt-test-generator/SKILL.md
```

Then prompt:

```text
Use the Prompt X-Ray workflow. First build a prompt brief, then audit the resulting prompt, then generate quality-check cases.
```

## Codex

Codex does not use Claude-style skill folders as the primary mechanism.

For Codex, use `AGENTS.md` as the bridge.

### Option 1: Add a repository-level AGENTS.md

Create or update `AGENTS.md` in the target repository:

```markdown
# AGENTS.md

## Prompt X-Ray Workflows

When working on prompts, system prompts, agent instructions, RAG policies, or structured LLM outputs, use the relevant workflow from `docs/prompt-xray-skills/`.

Recommended mapping:

- Vague prompt idea -> `01-prompt-brief-builder`
- Existing prompt review -> `02-prompt-auditor`
- Assistant behavior prompt -> `03-system-prompt-architect`
- Coding-agent instructions -> `04-agent-instruction-writer`
- Knowledge-base assistant -> `05-rag-answer-policy`
- JSON/API output -> `06-structured-output-designer`
- Prompt checks -> `07-prompt-test-generator`
- Bad model output -> `08-prompt-debugger`
- AI feature idea -> `09-prompt-to-product-spec`

Before editing production prompts:

1. Identify the prompt type.
2. Apply the relevant Prompt X-Ray workflow.
3. Keep changes minimal and testable.
4. Add at least one quality-check case.
5. Report assumptions and remaining risks.
```

Then copy the skill files into your repo:

```bash
mkdir -p docs/prompt-xray-skills
cp -r prompt-xray-skills/skills/* docs/prompt-xray-skills/
```

### Option 2: Use a single skill on demand

Paste the relevant `SKILL.md` into the Codex task prompt and say:

```text
Use the workflow below as the operating procedure for this task.
```

This is the simplest method when you do not want to add files to the target repo.

## Cursor

Cursor uses project rules stored in `.cursor/rules`.

To use Prompt X-Ray Skills in Cursor, convert a skill into an `.mdc` rule.

Example:

```text
.cursor/rules/prompt-auditor.mdc
```

Suggested content:

```mdc
---
description: Audit LLM prompts for ambiguity, missing context, instruction conflicts, weak output contracts, and poor testability.
globs: ["**/*.md", "**/*.mdx", "**/*.ts", "**/*.tsx"]
alwaysApply: false
---

When the user asks to improve, audit, debug, or harden an LLM prompt, follow the workflow from `skills/02-prompt-auditor/SKILL.md`.

First identify the prompt type, then check ambiguity, missing context, instruction conflicts, unsupported claims, output contract, and testability. Return a prompt audit report and an improved prompt.
```

Recommended setup:

```bash
mkdir -p .cursor/rules
mkdir -p docs/prompt-xray-skills
cp -r prompt-xray-skills/skills/* docs/prompt-xray-skills/
```

Then create small `.mdc` rules that point to the relevant full skill files.

Do not paste all skills into one always-on Cursor rule. Keep rules small and scoped.

## ChatGPT Projects

Use selected skills as project files or project instructions.

Recommended setup:

1. Create a Project named `Prompt X-Ray`.
2. Add selected `SKILL.md` files as project files.
3. Add examples from `examples/`.
4. Add a short project instruction:

```text
When I ask to write, improve, audit, debug, or test an LLM prompt, use the relevant Prompt X-Ray Skill workflow from the project files. Prefer prompt briefs, audits, structured outputs, and quality-check cases over generic prompt tips.
```

Suggested initial files:

```text
skills/01-prompt-brief-builder/SKILL.md
skills/02-prompt-auditor/SKILL.md
skills/03-system-prompt-architect/SKILL.md
skills/07-prompt-test-generator/SKILL.md
```

## Manual usage in any LLM

You can always paste a skill directly:

```text
Use the following SKILL.md as your operating procedure for this task:

<paste SKILL.md>

Task:
<a prompt or assistant idea>
```

## Recommended first installed skills

Start with only three:

```text
01-prompt-brief-builder
02-prompt-auditor
07-prompt-test-generator
```

These cover the core loop:

```text
brief -> prompt -> audit -> quality checks -> revision
```

Install the rest when you need more specialized workflows.

## Notes on skill design

Keep skills narrow.

Avoid loading every skill into every context.

Skills work best when each one has:

- a clear activation condition;
- a specific workflow;
- a concrete output format;
- a final checklist;
- examples or test cases.

## Security and trust note

Treat third-party skills as operational instructions, not passive documentation.

Before installing any external skill:

- read the full `SKILL.md`;
- check referenced scripts or files;
- avoid skills that ask for secrets or credentials;
- avoid skills that run destructive commands without explicit approval;
- install only the skills you actually need.

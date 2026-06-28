---
name: agent-instruction-writer
description: Write project-level instructions for coding agents and AI agents, including CLAUDE.md, AGENTS.md, Cursor rules, Codex instructions, and repository-specific agent behavior policies. Use this skill when a user wants an AI agent to work safely and consistently inside a codebase or workflow.
---

# Agent Instruction Writer Skill

## Purpose

Use this skill to create project-level instructions for AI agents.

The goal is to reduce agent drift, accidental rewrites, broken architecture, unsafe assumptions, and low-quality changes.

Good agent instructions are not motivational. They are operational rules for how the agent should work inside a specific project.

## When to use

Use this skill when the user wants to create or improve:

- `CLAUDE.md`;
- `AGENTS.md`;
- Cursor project rules;
- Codex instructions;
- coding-agent guidelines;
- repository-specific AI instructions;
- AI workflow rules for product, content, research, or support agents.

## Required input

Collect or infer:

- project purpose;
- tech stack;
- architecture overview;
- important directories;
- commands for install, dev, test, lint, build;
- do-not-touch zones;
- coding conventions;
- testing expectations;
- output/reporting format;
- known fragile areas.

If information is missing, mark placeholders instead of inventing details.

## Procedure

### 1. Identify the agent environment

Determine whether the instructions are for:

- Claude Code;
- Codex;
- Cursor;
- Aider;
- a custom agent;
- a general repository AI assistant.

If unknown, write platform-neutral instructions.

### 2. Define project context

Explain what the project does in 3-6 sentences.

Include:

- target users;
- business goal;
- main workflows;
- production risks.

### 3. Define architecture boundaries

List major directories and responsibilities.

Example:

```text
app/      UI and routes
lib/      shared business logic
api/      server endpoints
workers/  background jobs
```

Tell the agent where changes should and should not happen.

### 4. Define allowed behavior

Specify what the agent may do:

- make small focused changes;
- preserve existing architecture;
- add tests;
- update docs;
- ask for clarification when scope is unclear;
- explain trade-offs.

### 5. Define forbidden behavior

Specify what the agent must not do:

- rewrite unrelated files;
- change public APIs without instruction;
- modify secrets or credentials;
- remove error handling;
- add dependencies without justification;
- replace architecture without approval;
- silently ignore failing tests.

### 6. Define workflow

A good coding agent should:

1. Read relevant files first.
2. Summarize the intended change.
3. Make the smallest safe change.
4. Run or describe relevant checks.
5. Report what changed and what remains risky.

### 7. Define command policy

Include commands for:

- install;
- development;
- lint;
- typecheck;
- tests;
- build.

If commands are unknown, use placeholders.

### 8. Define testing policy

Specify:

- when tests are required;
- what to do if tests cannot be run;
- how to handle failing tests;
- whether snapshots, integration tests, or manual QA are expected.

### 9. Define reporting format

Require the agent to finish with:

- summary;
- files changed;
- checks run;
- risks;
- follow-up recommendations.

## Output format

Return a ready-to-copy instruction file:

```markdown
# Agent Instructions

## Project Overview

[Describe the project.]

## Tech Stack

- Runtime:
- Framework:
- Database:
- Auth:
- Deployment:
- Testing:

## Architecture Map

| Path | Responsibility |
|---|---|
| `...` | ... |

## Working Rules

The agent should:

- ...

The agent must not:

- ...

## Change Workflow

For every task:

1. Read relevant files before editing.
2. Identify the smallest safe change.
3. Preserve existing architecture unless explicitly asked to change it.
4. Update tests or explain why tests are not applicable.
5. Report changes clearly.

## Commands

```bash
# install

# development

# lint

# typecheck

# test

# build
```

## Testing Policy

- ...

## Risk Areas

- ...

## Response Format

After completing a task, respond with:

```markdown
## Summary

## Files Changed

## Checks Run

## Risks / Notes

## Suggested Next Steps
```
```

## Quality checklist

Before finalizing, verify:

- project context is specific;
- do-not-touch zones are clear;
- commands are present or marked as placeholders;
- reporting format is defined;
- forbidden behavior is concrete;
- the instructions reduce agent autonomy where risk is high.

## Boundaries

This skill writes agent instructions. It does not verify that a specific agent will always follow them. Test the instructions on real tasks and refine them based on observed failures.

# Skill Authoring Guide

This guide defines the house style for Prompt X-Ray skills.

## Skill folder structure

Each skill should live in its own folder:

```text
skills/01-skill-name/
  SKILL.md
```

Optional supporting files may be added later:

```text
skills/01-skill-name/
  SKILL.md
  examples.md
  checklist.md
  templates.md
```

## SKILL.md structure

Every `SKILL.md` should include:

1. Frontmatter
2. Purpose
3. When to use
4. Inputs
5. Procedure
6. Output format
7. Quality checks
8. Boundaries

## Frontmatter

Use this shape:

```yaml
---
name: skill-name
description: Short activation-focused description. Use this skill when...
---
```

The description should help the model know when to activate the skill.

Bad:

```yaml
description: A skill for prompts.
```

Good:

```yaml
description: Audit LLM prompts for ambiguity, missing context, instruction conflicts, hallucination risk, weak output contracts, and poor testability.
```

## Procedure style

Use step-by-step procedures.

Prefer verbs:

- classify;
- extract;
- identify;
- check;
- flag;
- rewrite;
- score;
- generate;
- validate.

Avoid vague instructions like:

- make it better;
- be creative;
- improve quality;
- use best practices.

## Output format

Every skill must define a concrete output format.

The output should be copyable and useful without additional explanation.

## Quality checks

Every skill should include a final checklist or validation section.

Examples:

- Is the goal explicit?
- Is the source of truth defined?
- Is the output format stable?
- Are missing-data cases handled?
- Is the result testable?

## Boundaries

Every skill should state what it does not guarantee.

Examples:

- The skill improves prompt reliability but does not guarantee factual correctness.
- The skill designs a schema but does not validate runtime integration.
- The skill creates tests but does not execute model evaluations.

## Naming conventions

Use lowercase kebab-case names:

```text
prompt-auditor
system-prompt-architect
rag-answer-policy
```

## Skill quality bar

A skill is ready when it can be used by a model to produce a useful artifact with minimal extra explanation.

A skill is not ready if it only gives generic advice.

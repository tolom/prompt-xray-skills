# Prompt X-Ray Skills

Reusable `SKILL.md` workflows for writing, auditing, testing, and hardening LLM prompts.

Most prompt engineering resources teach tips, tricks, and example prompts.

This repository takes a different approach:

> A prompt is a behavioral specification for an AI system.

Good prompts should be clear, structured, testable, reusable, and resistant to missing context, ambiguity, hallucination, weak output contracts, and instruction drift.

Prompt X-Ray Skills help you design prompts like small software systems.

## What this is

A collection of practical LLM skills for:

- turning rough ideas into prompt briefs;
- auditing weak prompts;
- designing system prompts;
- writing agent instructions;
- creating RAG answer policies;
- designing structured outputs;
- generating prompt test cases;
- debugging bad model responses;
- converting AI assistant ideas into product specifications.

## What this is not

This is not a list of magic prompts.

This is not a prompt marketplace.

This is not a collection of generic "act as..." templates.

The goal is not to make prompts longer.

The goal is to make prompts more reliable.

## Core philosophy

A good prompt should define:

1. Goal
2. Context
3. Role
4. Inputs
5. Constraints
6. Decision rules
7. Output format
8. Uncertainty behavior
9. Quality criteria
10. Test cases

If a prompt cannot be tested, it is not production-ready.

## Skills included

```text
skills/
  01-prompt-brief-builder/
  02-prompt-auditor/
  03-system-prompt-architect/
  04-agent-instruction-writer/
  05-rag-answer-policy/
  06-structured-output-designer/
  07-prompt-test-generator/
  08-prompt-debugger/
  09-prompt-to-product-spec/
```

## Recommended workflow

1. Start with `01-prompt-brief-builder` when the task is still vague.
2. Write or improve the prompt.
3. Run `02-prompt-auditor` to identify fragility.
4. Use `07-prompt-test-generator` to create test cases.
5. Use `06-structured-output-designer` when the output must be consumed by software.
6. Use `08-prompt-debugger` when real outputs fail.
7. Convert stable workflows into specs or agent rules when needed.

## Who this is for

- AI builders
- developers using coding agents
- prompt engineers
- AI consultants
- product managers
- automation specialists
- founders building AI-powered products
- teams using LLMs in real workflows

## How to use these skills

Each skill is a folder containing a `SKILL.md` file.

You can copy a skill folder into an LLM environment that supports skill-style workflows, or simply paste the `SKILL.md` instructions into your AI workspace when you need that workflow.

The skills are intentionally practical and implementation-oriented. They are designed to produce usable artifacts: prompt briefs, audits, rewritten prompts, schemas, test cases, policies, and product specs.

## Design principles

See [`docs/principles.md`](docs/principles.md).

## Authoring guide

See [`docs/skill-authoring-guide.md`](docs/skill-authoring-guide.md).

## Examples

See [`examples/`](examples/).

## License

MIT

---
name: prompt-xray-skills
description: Route prompt-engineering tasks to the right Prompt X-Ray workflow. Use this skill when the user wants to write, audit, test, debug, structure, or productize LLM prompts, system prompts, RAG policies, agent instructions, structured outputs, or AI assistant ideas.
---

# Prompt X-Ray Skills Router

## Purpose

Use this root skill as a router for the Prompt X-Ray skill pack.

The goal is to choose the right prompt-engineering workflow and apply it consistently.

Do not treat this repository as a list of prompt templates. Treat it as a set of workflows for designing reliable LLM behavior.

## Core principle

A prompt is a behavioral specification for an AI system.

A good prompt should usually define:

1. Goal
2. Context
3. Role
4. Inputs
5. Constraints
6. Source of truth
7. Decision rules
8. Output format
9. Uncertainty behavior
10. Quality checks

If a prompt cannot be tested, it is not production-ready.

## Available workflows

Use these internal skills depending on the task.

### 01-prompt-brief-builder

Use when the user has a vague idea and needs a structured prompt brief before writing the final prompt.

Typical triggers:

- "Help me write a prompt"
- "I need an AI assistant that..."
- "Turn this idea into a prompt"
- "I don't know how to explain this to an LLM"

Output:

- prompt brief;
- inputs;
- source of truth;
- constraints;
- output format;
- test cases.

### 02-prompt-auditor

Use when the user provides an existing prompt and wants to improve, harden, debug, or make it more reliable.

Typical triggers:

- "Improve this prompt"
- "Audit this prompt"
- "Make this prompt production-ready"
- "Why is this prompt unreliable?"

Output:

- prompt audit report;
- main problems;
- missing information;
- risk areas;
- improved prompt;
- test cases.

### 03-system-prompt-architect

Use when the user needs a system prompt for an assistant, chatbot, internal tool, or workflow agent.

Typical triggers:

- "Create a system prompt"
- "Write instructions for an AI assistant"
- "Design assistant behavior"
- "Make a prompt for a support bot"

Output:

- system prompt;
- mission;
- scope;
- source-of-truth policy;
- workflow;
- uncertainty rules;
- output contract.

### 04-agent-instruction-writer

Use when the user needs instructions for coding agents or project agents.

Typical triggers:

- "Write AGENTS.md"
- "Create CLAUDE.md"
- "Make Cursor rules"
- "Prepare Codex instructions"
- "Tell the coding agent how to work in this repo"

Output:

- repository-level agent instructions;
- architecture map;
- allowed/forbidden behavior;
- command policy;
- testing policy;
- reporting format.

### 05-rag-answer-policy

Use when the prompt is for a knowledge-base assistant or RAG system.

Typical triggers:

- "Make a RAG prompt"
- "The bot should answer only from docs"
- "Define no-answer behavior"
- "Prevent unsupported answers"

Output:

- source priority;
- citation rules;
- insufficient-context behavior;
- conflicting-source behavior;
- escalation rules.

### 06-structured-output-designer

Use when the LLM output must be parsed, stored, validated, or consumed by software.

Typical triggers:

- "Return JSON"
- "Create a schema"
- "Extract fields"
- "Make CRM-ready output"
- "Design structured output"

Output:

- output schema;
- field definitions;
- validation rules;
- valid example;
- insufficient-context example.

### 07-prompt-test-generator

Use when the user needs test cases or quality checks for a prompt.

Typical triggers:

- "Test this prompt"
- "Generate evals"
- "Create edge cases"
- "How do I check if this prompt works?"

Output:

- quality-check suite;
- typical cases;
- edge cases;
- incomplete-context cases;
- ambiguous cases;
- format-stability cases;
- review criteria.

### 08-prompt-debugger

Use when the prompt is already producing bad outputs and the user wants to diagnose the cause.

Typical triggers:

- "The model ignores my format"
- "This output is too generic"
- "Why is this answer bad?"
- "Debug this prompt"

Output:

- debug report;
- expected vs actual behavior;
- likely causes;
- smallest useful fix;
- revised prompt;
- confirmation test.

### 09-prompt-to-product-spec

Use when a prompt or assistant idea should become a product specification or MVP task.

Typical triggers:

- "Turn this AI idea into a spec"
- "Create a product spec for this assistant"
- "Convert this prompt into a product feature"
- "Prepare this for a developer"

Output:

- product specification;
- users and roles;
- AI responsibilities;
- human responsibilities;
- MVP scope;
- data sources;
- acceptance criteria;
- risks.

## Routing procedure

When the user asks for prompt-engineering help:

1. Identify the task type.
2. Select the most relevant internal skill.
3. If the request is vague, start with `01-prompt-brief-builder`.
4. If the user provides an existing prompt, use `02-prompt-auditor`.
5. If the output must be consumed by software, include `06-structured-output-designer`.
6. If the prompt will be reused, include `07-prompt-test-generator`.
7. If the user wants implementation planning, use `09-prompt-to-product-spec`.
8. Produce a concrete artifact, not generic advice.

## Common chains

### Vague prompt idea

```text
01-prompt-brief-builder -> 02-prompt-auditor -> 07-prompt-test-generator
```

### Assistant system prompt

```text
01-prompt-brief-builder -> 03-system-prompt-architect -> 02-prompt-auditor
```

### Coding agent instructions

```text
04-agent-instruction-writer -> 02-prompt-auditor -> 07-prompt-test-generator
```

### RAG assistant

```text
05-rag-answer-policy -> 03-system-prompt-architect -> 07-prompt-test-generator
```

### Structured extraction/API output

```text
06-structured-output-designer -> 02-prompt-auditor -> 07-prompt-test-generator
```

### Broken prompt output

```text
08-prompt-debugger -> 02-prompt-auditor -> 07-prompt-test-generator
```

### Prompt idea to MVP

```text
01-prompt-brief-builder -> 09-prompt-to-product-spec
```

## Output rules

When applying a workflow:

- produce the requested artifact directly;
- avoid generic prompt tips;
- mark assumptions clearly;
- separate stable instructions from variable inputs;
- define missing-information behavior;
- include output format when relevant;
- include quality checks for reusable prompts;
- prefer practical examples over theory.

## Default behavior

If the user does not specify a format, return:

1. Diagnosis or brief summary
2. Main artifact
3. Quality checklist
4. Suggested next step

## Boundaries

This skill routes prompt-engineering workflows. It does not guarantee identical model behavior across platforms. Always test important prompts with realistic inputs before production use.

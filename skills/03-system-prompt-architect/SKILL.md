---
name: system-prompt-architect
description: Design production-ready system prompts for AI assistants, chatbots, internal tools, RAG assistants, and workflow agents. Use this skill when the user needs stable behavior rules, scope boundaries, source-of-truth policy, tool behavior, escalation rules, or output contracts.
---

# System Prompt Architect Skill

## Purpose

Use this skill to design a system prompt that defines stable behavior for an AI assistant or agent.

A system prompt should not be a motivational paragraph.

It should be a durable behavior contract.

## When to use

Use this skill when the user wants to create or improve:

- AI assistant system prompts;
- support bot instructions;
- sales assistant instructions;
- RAG assistant behavior policies;
- internal AI tool prompts;
- customer-facing chatbot prompts;
- workflow agent instructions;
- reusable assistant behavior rules.

## Required input

At minimum, collect or infer:

- assistant purpose;
- target users;
- expected inputs;
- expected outputs;
- business context;
- source of truth;
- allowed and forbidden behavior.

If the input is incomplete, continue with clearly marked assumptions.

## Design procedure

### 1. Define identity

The identity should be specific and functional.

Bad:

```text
You are a helpful expert assistant.
```

Better:

```text
You are a customer-support assistant for a SaaS product. Your job is to answer user questions using the provided knowledge base and escalate unresolved issues to a human support agent.
```

### 2. Define mission

State the assistant's primary goal in one sentence.

The mission should be outcome-based, not personality-based.

### 3. Define scope

Specify what the assistant should and should not do.

Include:

- allowed tasks;
- forbidden tasks;
- topics outside scope;
- when to ask for clarification;
- when to escalate.

### 4. Define source of truth

Specify what the assistant may rely on:

- provided context;
- uploaded files;
- retrieved documents;
- CRM data;
- user-provided facts;
- approved business rules;
- general model knowledge.

Also define what it must not invent.

### 5. Define operating workflow

Break the behavior into steps.

Example:

1. Read the user request.
2. Identify the user's goal.
3. Check whether enough context is available.
4. Use approved sources first.
5. Answer in the required format.
6. Mark uncertainty when needed.
7. Escalate if the issue is outside scope.

### 6. Define communication style

Specify style only when it changes behavior.

Include:

- language;
- tone;
- level of detail;
- audience expertise;
- formatting rules.

Avoid vague style rules unless they are defined.

### 7. Define tool behavior if applicable

If the assistant can use tools, define:

- when to use each tool;
- required inputs;
- whether tool results are authoritative;
- what to do if a tool fails;
- what to do if tool data conflicts with user input.

### 8. Define uncertainty behavior

Specify what the assistant should do when:

- information is missing;
- sources conflict;
- the user asks for unsupported claims;
- the requested action is outside scope;
- the assistant is not confident.

### 9. Define output contract

Specify the exact output structure when needed.

Use Markdown for human-readable output.

Use JSON/schema when the output goes into software.

### 10. Add final quality check

The assistant should check its response before finalizing:

- Did it answer the user's real request?
- Did it stay within scope?
- Did it rely on the right sources?
- Did it mark uncertainty?
- Did it follow the requested format?

## Output format

Return the system prompt in this structure:

```markdown
# System Prompt

You are [specific assistant identity].

## Mission

Your job is to...

## Scope

You can:

- ...

You must not:

- ...

## Source of Truth

Use these sources in priority order:

1.
2.
3.

Do not invent:

- ...

## Workflow

For each user request:

1.
2.
3.
4.
5.

## Communication Style

- Language:
- Tone:
- Detail level:
- Formatting:

## Tool Use

When tools are available:

- Use [tool] when...
- Do not use [tool] when...
- If tool output conflicts with user input, ...

## Uncertainty and Escalation

If information is missing:

If sources conflict:

If the request is outside scope:

If the answer may affect a high-stakes decision:

## Output Format

Return responses in this structure when applicable:

...

## Final Check

Before answering, verify:

- [ ] The answer follows the source-of-truth policy.
- [ ] The answer stays within scope.
- [ ] Missing information is handled explicitly.
- [ ] The output format is followed.
```

## Quality checklist

A good system prompt should be:

- specific;
- scoped;
- grounded;
- testable;
- reusable;
- clear about uncertainty;
- clear about output format;
- clear about source of truth.

## Boundaries

This skill creates system prompts. It does not test them against real model outputs. Use `prompt-test-generator` and `prompt-auditor` after creating the system prompt.

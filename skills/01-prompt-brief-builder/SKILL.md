---
name: prompt-brief-builder
description: Convert rough task descriptions into structured prompt briefs. Use this skill when the user wants to create a high-quality prompt but only has a vague idea, business task, assistant concept, automation idea, or desired output.
---

# Prompt Brief Builder Skill

## Purpose

Use this skill to transform a vague request into a structured prompt brief.

A prompt brief is not the final prompt.

It is the specification that should exist before writing a reliable prompt.

## When to use

Use this skill when the user says things like:

- help me write a prompt;
- create a prompt for this task;
- I need an assistant that does this;
- turn this idea into a prompt;
- make a system prompt;
- prepare instructions for an AI agent;
- I want the model to generate better results;
- I do not know how to explain the task to an LLM.

## Core principle

Do not start by writing the final prompt.

First, clarify the task structure.

A good prompt brief should define:

1. Goal
2. User
3. Model role
4. Context
5. Inputs
6. Workflow
7. Constraints
8. Output format
9. Quality criteria
10. Failure behavior
11. Test cases

## Procedure

### 1. Extract the task

Restate the task in one sentence:

```text
The model should help [target user] achieve [goal] using [input/context] and return [output].
```

### 2. Identify the user and audience

Clarify:

- who will use the output;
- who the output is for;
- whether the output should be technical, business, educational, creative, operational, or customer-facing.

### 3. Identify the model role

Define the model's role only if it improves behavior.

Avoid generic roles like:

- "You are an expert";
- "You are the best";
- "You are a genius".

Prefer specific roles:

- "You are a B2B sales research assistant";
- "You are a product-specification assistant";
- "You are a support-answer policy engine";
- "You are a coding-agent reviewer".

### 4. Define input data

List the data the model will receive:

- user text;
- files;
- website content;
- CRM record;
- customer message;
- code;
- database fields;
- transcript;
- previous conversation;
- retrieved documents.

For each input, define whether it is required or optional.

### 5. Define source of truth

Specify what the model should rely on:

- provided context only;
- uploaded files;
- retrieved documents;
- external search;
- internal business rules;
- user-provided facts;
- model knowledge.

Also define what the model must not invent.

### 6. Define workflow

Break the task into steps.

Example:

1. Read the user input.
2. Extract key facts.
3. Identify missing information.
4. Decide whether there is enough context.
5. Generate the output.
6. Run a final quality check.

### 7. Define constraints

Specify:

- tone;
- language;
- length;
- formatting;
- forbidden content;
- required sections;
- business rules;
- privacy limits;
- uncertainty behavior.

### 8. Define output format

Choose the format:

- plain text;
- Markdown;
- table;
- JSON;
- structured report;
- checklist;
- email draft;
- product spec;
- code block;
- schema-compliant object.

If the output will be consumed by software, recommend structured JSON.

### 9. Define quality criteria

List what a good result must satisfy:

- accurate;
- grounded in input;
- complete;
- concise;
- follows format;
- does not invent missing facts;
- handles edge cases;
- useful for the next action.

### 10. Define failure behavior

Specify what the model should do when:

- input is incomplete;
- sources conflict;
- the task is ambiguous;
- the requested output is impossible;
- there is not enough evidence;
- the user asks for unsupported claims.

### 11. Create test cases

Generate:

- normal case;
- edge case;
- missing-context case;
- ambiguous case;
- bad-input case.

## Output format

Return the result as:

```markdown
# Prompt Brief

## One-sentence task

The model should...

## Use Case

- User:
- Audience:
- Business goal:
- Output goal:

## Model Role

The model should act as...

## Inputs

| Input | Required | Notes |
|---|---:|---|

## Source of Truth

The model should rely on:

The model must not invent:

## Workflow

1.
2.
3.
4.
5.

## Constraints

- Language:
- Tone:
- Length:
- Format:
- Forbidden actions:
- Required behavior:

## Output Format

Define the exact output structure here.

## Quality Criteria

- [ ] Criterion
- [ ] Criterion
- [ ] Criterion

## Failure Behavior

When information is missing, the model should...

When sources conflict, the model should...

When the request is ambiguous, the model should...

## Test Cases

### Normal case

Input:
Expected output:

### Edge case

Input:
Expected output:

### Missing-context case

Input:
Expected output:

## Next Step

After creating the brief, use it to write the final prompt or pass it into another skill such as `system-prompt-architect`, `prompt-auditor`, or `prompt-test-generator`.
```

## Quality check

Before finalizing, verify:

- the task is specific;
- the source of truth is explicit;
- inputs are defined;
- the output format is clear;
- missing-data behavior is defined;
- the prompt brief can be used to write a real prompt.

## Boundaries

This skill creates a prompt brief. It does not guarantee that the final prompt will work without testing.

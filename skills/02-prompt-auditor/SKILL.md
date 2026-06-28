---
name: prompt-auditor
description: Audit LLM prompts for ambiguity, missing context, instruction conflicts, hallucination risk, weak output contracts, and poor testability. Use this skill when the user provides a prompt and asks to improve, debug, harden, evaluate, or make it production-ready.
---

# Prompt Auditor Skill

## Purpose

Use this skill to audit an existing LLM prompt and identify why it may fail.

The goal is not only to rewrite the prompt.

The goal is to make the prompt clearer, safer, more testable, more reusable, and more reliable across repeated use.

## When to use

Use this skill when the user asks to:

- improve a prompt;
- audit a prompt;
- debug poor model output;
- reduce hallucinations;
- make a prompt more reliable;
- make a prompt production-ready;
- adapt a prompt for an assistant, agent, RAG system, workflow, or API;
- evaluate whether a prompt is clear enough for repeated use.

## Required input

The user should provide at least one of:

- an existing prompt;
- a rough instruction;
- a bad model output;
- a description of the task the prompt should perform.

Do not stop if some information is missing. Continue the audit and mark assumptions clearly.

## Preferred input

Ask for or infer when available:

1. Intended use case.
2. Target model or platform.
3. Expected input data.
4. Desired output format.
5. Examples of good outputs.
6. Examples of bad outputs.
7. Known failure cases.
8. Business or product constraints.
9. Whether the prompt is for chat, API, RAG, extraction, coding, sales, support, or an autonomous agent.

## Audit procedure

### 1. Classify the prompt

Identify the prompt type:

- one-shot prompt;
- reusable workflow prompt;
- system prompt;
- developer instruction;
- agent instruction;
- coding-agent rules;
- RAG answer policy;
- extraction prompt;
- classification prompt;
- content-generation prompt;
- sales/support assistant prompt;
- product-spec generation prompt.

### 2. Identify the intended behavior

Extract the intended behavior in plain language:

- What should the model do?
- For whom?
- Using what input?
- Under what constraints?
- What should the output look like?
- What should happen if information is missing?

If the intended behavior is unclear, mark this as a major issue.

### 3. Check ambiguity

Look for vague or overloaded words such as:

- improve;
- analyze;
- optimize;
- make better;
- professional;
- detailed;
- short;
- creative;
- high quality;
- modern;
- useful;
- relevant.

For each ambiguous phrase, explain what the model may interpret incorrectly.

### 4. Check missing context

Check whether the prompt defines:

- goal;
- audience;
- user role;
- model role;
- business context;
- input data;
- source of truth;
- constraints;
- forbidden actions;
- desired output;
- edge cases;
- uncertainty behavior;
- escalation behavior;
- examples.

### 5. Check instruction conflicts

Look for conflicts between:

- short and detailed;
- creative and strict;
- autonomous and safe;
- friendly and formal;
- generic and personalized;
- JSON output and prose explanation;
- source-grounded answering and external knowledge;
- speed and deep reasoning;
- broad task scope and narrow output format.

### 6. Check hallucination risk

Flag any part where the model may invent:

- facts;
- prices;
- sources;
- customer data;
- technical capabilities;
- implementation details;
- legal, medical, financial, or policy-sensitive claims;
- user preferences;
- company information;
- product features.

For each risk, define what the model should do instead.

### 7. Check output contract

Evaluate whether the prompt defines:

- required sections;
- section order;
- length limits;
- formatting rules;
- JSON/schema requirements;
- citation rules;
- examples;
- acceptance criteria;
- final checklist.

If the output must be used by software, recommend structured output.

### 8. Check testability

A production prompt should be testable.

Check whether it is possible to create:

- normal case;
- edge case;
- missing-context case;
- ambiguous-input case;
- conflicting-instruction case;
- bad-input case.

If not, explain what is missing.

## Scoring

Score the prompt from 0 to 10 on:

- Clarity
- Context completeness
- Constraint quality
- Output contract
- Hallucination resistance
- Testability
- Reusability

Then give one verdict:

- Production-ready
- Good but needs tightening
- Risky
- Too vague to reuse

## Output format

Return the audit in this structure:

```markdown
# Prompt Audit Report

## Verdict

- Overall verdict:
- Total score:
- One-sentence summary:

## Prompt Type

- Type:
- Intended use:
- Target output:

## Main Problems

### 1. Problem name

- Severity:
- Evidence:
- Why it matters:
- Fix:

## Missing Information

- [ ] Missing item
- [ ] Missing item
- [ ] Missing item

## Hallucination Risks

| Risk | Why it may happen | How to reduce it |
|---|---|---|

## Instruction Conflicts

| Conflict | Impact | Resolution |
|---|---|---|

## Improved Prompt

```text
<rewritten prompt>
```

## Test Cases

### Normal case

Input:
Expected behavior:

### Edge case

Input:
Expected behavior:

### Missing-context case

Input:
Expected behavior:

### Bad-input case

Input:
Expected behavior:

## Final Checklist

- [ ] Goal is explicit
- [ ] Context is sufficient
- [ ] Role is clear
- [ ] Constraints are concrete
- [ ] Output format is defined
- [ ] Missing-information behavior is defined
- [ ] Hallucination risks are reduced
- [ ] Prompt can be tested
```

## Rewrite rules

When rewriting:

- preserve the user's original intent;
- do not invent business details;
- clearly mark assumptions;
- separate role, task, context, constraints, and output format;
- define behavior when data is missing;
- prefer concrete rules over vague adjectives;
- keep the prompt reusable;
- make it easy to test repeatedly.

## Boundaries

This skill improves prompt reliability. It does not guarantee factual correctness, legal compliance, safety compliance, or identical behavior across all models.

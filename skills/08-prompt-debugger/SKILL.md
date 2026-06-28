---
name: prompt-debugger
description: Diagnose poor LLM outputs by comparing the prompt, input, expected output, and actual output. Use this skill when a prompt is already being used but the model response is wrong, vague, off-format, too generic, overconfident, or not useful.
---

# Prompt Debugger Skill

## Purpose

Use this skill to diagnose why a prompt produced a poor result.

The goal is to identify the likely failure cause before rewriting the prompt.

Do not randomly rewrite the prompt without analyzing the failure.

## When to use

Use this skill when the user says:

- the prompt does not work;
- the model output is bad;
- the output is too generic;
- the model ignores the format;
- the assistant gives wrong or unsupported details;
- the prompt works sometimes but not consistently;
- the output is not useful for the workflow.

## Required input

Ask for or infer:

- current prompt;
- user input;
- actual model output;
- expected output;
- target model/platform;
- known constraints;
- whether the output is for a human or software.

If actual output is not available, run a structural diagnosis of the prompt instead.

## Diagnosis procedure

### 1. Identify the observed failure

Classify the issue:

- unclear task;
- missing context;
- weak role;
- conflicting instructions;
- poor output format;
- insufficient examples;
- unsupported claims;
- too much freedom;
- wrong level of detail;
- bad input data;
- model limitation;
- tool/source limitation.

### 2. Compare expected vs actual behavior

Write the difference in plain language.

Example:

```text
Expected: concise JSON extraction.
Actual: long Markdown explanation with extra fields.
```

### 3. Identify prompt-level causes

Look for:

- vague verbs;
- missing constraints;
- missing source-of-truth policy;
- missing output contract;
- missing examples;
- no incomplete-data behavior;
- too many goals in one instruction.

### 4. Identify context-level causes

Check whether the input provided enough information.

If the prompt asks the model to infer unavailable facts, mark this as a context problem, not only a prompt problem.

### 5. Identify output-contract causes

If the issue is formatting, check whether the prompt defines:

- exact sections;
- JSON keys;
- field types;
- required vs optional fields;
- examples;
- no-extra-text rules.

### 6. Recommend the smallest fix

Prefer small targeted changes:

- add a missing rule;
- add output format;
- add incomplete-context behavior;
- add examples;
- split the task;
- add a test case;
- define source of truth.

Do not rewrite everything unless necessary.

### 7. Create a revised prompt

Rewrite the prompt only after the diagnosis.

### 8. Create a confirmation test

Add one test case that would verify the fix.

## Output format

Return the diagnosis as:

```markdown
# Prompt Debug Report

## Observed Problem

- Expected behavior:
- Actual behavior:
- Main failure type:

## Likely Causes

### 1. Cause name

- Evidence:
- Why it matters:
- Fix:

## Prompt-Level Issues

- ...

## Context-Level Issues

- ...

## Output-Format Issues

- ...

## Smallest Useful Fix

...

## Revised Prompt

```text
<revised prompt>
```

## Confirmation Test

**Input**

```text
...
```

**Expected behavior**

...

## Follow-Up Improvements

- ...
```

## Quality checklist

A good debug report should:

- separate prompt issues from context issues;
- identify the actual failure type;
- recommend the smallest fix;
- include a revised prompt;
- include a confirmation test.

## Boundaries

This skill diagnoses prompt behavior based on available examples. It does not guarantee that the revised prompt will work across all models without testing.

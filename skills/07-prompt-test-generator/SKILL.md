---
name: prompt-test-generator
description: Generate practical quality-check cases for LLM prompts, including typical inputs, edge inputs, ambiguous requests, incomplete context, expected behavior, and review criteria. Use this skill when a prompt needs to be validated before reuse or production.
---

# Prompt Test Generator Skill

## Purpose

Use this skill to create a practical quality-check suite for an LLM prompt.

The goal is to see whether the prompt behaves consistently under realistic inputs.

A prompt that cannot be checked is not production-ready.

## When to use

Use this skill when the user asks to:

- test a prompt;
- create prompt evals;
- check whether a prompt is reliable;
- generate edge cases;
- validate a system prompt;
- compare prompt versions;
- prepare a prompt for production.

## Required input

The user should provide:

- the prompt to check;
- intended use case;
- expected output format;
- target audience;
- known quality concerns if available.

If some inputs are missing, infer likely cases and mark assumptions.

## Procedure

### 1. Identify prompt type

Classify the prompt as one of:

- content generation;
- extraction;
- classification;
- RAG answer;
- system prompt;
- agent instruction;
- coding-agent prompt;
- sales/support prompt;
- product-spec prompt.

### 2. Define success behavior

Extract what a successful output should do.

Define:

- required output structure;
- correctness criteria;
- tone/format criteria;
- grounding criteria;
- incomplete-information behavior.

### 3. Generate typical cases

Create common inputs the prompt should handle well.

### 4. Generate edge cases

Create uncommon but realistic inputs:

- very short input;
- long input;
- mixed language;
- incomplete but usable data;
- multiple requests in one message.

### 5. Generate incomplete-context cases

Create inputs where important details are missing.

Expected behavior should be explicit uncertainty, assumptions, partial output, or a clarifying question.

### 6. Generate ambiguous cases

Create inputs that can be interpreted in more than one way.

Expected behavior should usually be clarification or clearly marked assumptions.

### 7. Generate format-stability cases

Create inputs that might cause the model to ignore the requested output format.

Expected behavior should preserve the required format.

### 8. Define review criteria

For each case, define concrete review criteria.

Avoid vague criteria such as "good answer".

## Output format

Return the quality-check suite as:

```markdown
# Prompt Quality-Check Suite

## Prompt Type

- Type:
- Intended use:
- Main quality risk:

## Success Criteria

- [ ] Output follows the required format.
- [ ] Answer is grounded in provided context.
- [ ] Missing information is handled explicitly.
- [ ] Ambiguity is handled explicitly.
- [ ] Constraints are followed.

## Cases

### Case 1: Typical input

**Input**

```text
...
```

**Expected behavior**

...

**Review criteria**

- ...

### Case 2: Edge input

**Input**

```text
...
```

**Expected behavior**

...

**Review criteria**

- ...

### Case 3: Incomplete context

**Input**

```text
...
```

**Expected behavior**

...

**Review criteria**

- ...

### Case 4: Ambiguous request

**Input**

```text
...
```

**Expected behavior**

...

**Review criteria**

- ...

### Case 5: Format stability

**Input**

```text
...
```

**Expected behavior**

...

**Review criteria**

- ...

## Coverage Notes

- Covered risks:
- Uncovered risks:
- Recommended next checks:
```

## Quality checklist

A good prompt quality-check suite should include:

- typical cases;
- edge cases;
- incomplete-context cases;
- ambiguous cases;
- format-stability cases;
- concrete review criteria.

## Boundaries

This skill creates quality-check cases. It does not execute model evaluations automatically.

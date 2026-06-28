---
name: structured-output-designer
description: Design reliable structured outputs for LLM workflows, including JSON schemas, extraction objects, classification results, CRM fields, tables, and API-ready response contracts. Use this skill when the model output must be parsed, stored, validated, or consumed by software.
---

# Structured Output Designer Skill

## Purpose

Use this skill to design a stable output contract for LLM-generated data.

The goal is to make model output easier to parse, validate, store, and test.

If an LLM output is consumed by software, the prompt should not rely on loosely formatted prose.

## When to use

Use this skill when the user needs:

- JSON output;
- schema-compliant output;
- extraction fields;
- classification labels;
- CRM-ready data;
- API response objects;
- tables with fixed columns;
- validation rules;
- deterministic output structure.

## Required input

Collect or infer:

- what the output will be used for;
- whether a human or software will consume it;
- required fields;
- optional fields;
- field types;
- allowed values;
- validation rules;
- error/fallback behavior.

## Procedure

### 1. Identify the consumer

Determine who or what will consume the output:

- human reader;
- frontend UI;
- backend service;
- database;
- CRM;
- spreadsheet;
- workflow automation;
- another LLM.

### 2. Define the object purpose

State what the structured output represents.

Example:

```text
This object represents a qualified sales lead extracted from a company website.
```

### 3. Define fields

For each field, define:

- name;
- type;
- required/optional;
- description;
- allowed values;
- fallback value;
- validation rule.

### 4. Define enums

Use enums for classification fields.

Bad:

```text
Return the lead quality as text.
```

Better:

```text
lead_quality must be one of: low, medium, high, unknown.
```

### 5. Define uncertainty fields

Structured outputs should make uncertainty visible.

Useful fields:

- confidence;
- missing_information;
- assumptions;
- source_notes;
- requires_human_review;

### 6. Define error output

Specify what to return when input is invalid or insufficient.

Example:

```json
{
  "status": "insufficient_context",
  "missing_information": ["company website", "target offer"],
  "result": null
}
```

### 7. Add examples

Provide at least one valid output example and one insufficient-context example.

### 8. Add prompt instructions

Write the prompt instructions that force the model to follow the schema.

## Output format

Return the result in this structure:

```markdown
# Structured Output Contract

## Purpose

This output represents...

## Consumer

The output will be consumed by...

## Schema

```json
{
  "type": "object",
  "required": [],
  "properties": {}
}
```

## Field Definitions

| Field | Type | Required | Description | Fallback |
|---|---|---:|---|---|

## Allowed Values

- field_name: value_1 | value_2 | value_3

## Invalid or Insufficient Input Behavior

If input is insufficient, return:

```json
{
  "status": "insufficient_context",
  "missing_information": [],
  "result": null
}
```

## Prompt Instructions

```text
Return only a JSON object that matches the schema. Do not include markdown, prose, explanations, or extra keys.
```

## Valid Example

```json
{}
```

## Insufficient Context Example

```json
{}
```

## Validation Checklist

- [ ] All required fields are defined.
- [ ] Optional fields have fallback behavior.
- [ ] Enums are explicit.
- [ ] Missing context is represented.
- [ ] Output can be parsed by software.
```

## Quality checklist

A good structured output contract should be:

- parseable;
- minimal;
- explicit;
- validated;
- tolerant of missing context;
- stable across repeated calls.

## Boundaries

This skill designs output contracts. It does not guarantee runtime validation unless a parser or schema validator is implemented.

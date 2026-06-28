# Prompt X-Ray Principles

Prompt X-Ray Skills are based on one core idea:

> A prompt is not a magic phrase. It is a behavioral specification for an AI system.

This document defines the principles used across all skills in this repository.

## 1. Prompt as specification

A production prompt should define behavior, not only intent.

A reliable prompt usually includes:

- goal;
- context;
- role;
- inputs;
- source of truth;
- constraints;
- decision rules;
- output contract;
- uncertainty behavior;
- test cases.

If the desired behavior is not specified, the model will infer it. Inference may be useful for exploration, but it is risky in repeatable workflows.

## 2. Context before clever wording

Better prompts usually come from better context structure, not from secret phrases.

Prefer:

- clear sections;
- stable instructions;
- explicit input blocks;
- examples;
- known failure cases;
- quality criteria.

Avoid relying on vague quality adjectives such as "professional", "better", "modern", "creative", or "detailed" without defining what they mean.

## 3. Stable instructions and variable data should be separated

A reusable prompt should separate:

- stable behavior rules;
- user input;
- retrieved context;
- examples;
- output schema;
- runtime constraints.

This improves maintainability, testing, and reuse.

## 4. Output should have a contract

If the output is consumed by humans, define readable structure.

If the output is consumed by software, define a schema.

Weak instruction:

```text
Return useful information about the customer.
```

Better instruction:

```text
Return a JSON object with: customer_type, pain_points, urgency_score, next_action, missing_information.
```

## 5. Missing information behavior must be explicit

A good prompt tells the model what to do when context is incomplete.

Common options:

- ask a clarifying question;
- state an assumption;
- return a partial result;
- mark uncertainty;
- refuse to infer;
- escalate to a human;
- request a required input.

Without this rule, the model may invent missing details.

## 6. Use examples when rules are not enough

Examples are useful when the desired behavior is hard to describe abstractly.

Use examples for:

- tone;
- classification;
- extraction;
- formatting;
- edge cases;
- good vs bad outputs;
- boundary decisions.

A good example should teach the pattern, not just decorate the prompt.

## 7. Prompts should be testable

If a prompt cannot be tested, it is not production-ready.

At minimum, create tests for:

- normal input;
- edge input;
- missing context;
- conflicting instructions;
- bad input;
- hallucination-prone input.

Each test should define expected behavior.

## 8. Prompt quality is measured by behavior

A prompt is good only if it reliably produces useful behavior under real inputs.

Do not judge a prompt only by how polished it looks.

Judge it by:

- clarity;
- repeatability;
- robustness;
- testability;
- output usability;
- failure handling.

## 9. Prompts should be iterated with failure analysis

The workflow should be:

```text
prompt -> output -> failure analysis -> prompt revision -> tests -> repeat
```

Do not rewrite prompts randomly. Diagnose failure modes first.

## 10. Prompt engineering is product design

For real workflows, prompts are part of a larger system:

- product goal;
- user journey;
- data sources;
- UI;
- tools;
- permissions;
- monitoring;
- evaluation;
- escalation.

A prompt that works in a chat window may still fail as a product feature.

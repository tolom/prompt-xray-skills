# Prompt X-Ray Examples

Use these examples as starting points for common LLM product work.

The goal is not to copy a perfect prompt. The goal is to see how weak or vague instructions become clearer, testable, reusable prompt workflows.

## Start here

| Example | Use when you need to... | File |
|---|---|---|
| Simple support prompt | Turn a vague support prompt into a reliable assistant behavior spec | [`before-after/simple-support-prompt.md`](before-after/simple-support-prompt.md) |
| Lead research prompt | Improve a lead-research prompt so it produces more useful, structured results | [`before-after/lead-research-prompt.md`](before-after/lead-research-prompt.md) |
| Prompt brief builder | Turn a rough idea into a structured prompt brief before writing the final prompt | [`before-after/prompt-brief-builder-example.md`](before-after/prompt-brief-builder-example.md) |
| Business assistant system prompt | Design a production-style system prompt for an AI business assistant | [`business-assistant/system-prompt.md`](business-assistant/system-prompt.md) |
| Coding agent instructions | Create repository-level instructions for coding agents such as Claude Code, Codex, or Cursor | [`coding-agent/AGENTS.md`](coding-agent/AGENTS.md) |
| RAG support answer policy | Define source-of-truth, citation, no-answer, and escalation behavior for RAG systems | [`rag-assistant/support-answer-policy.md`](rag-assistant/support-answer-policy.md) |
| Lead qualification schema | Design structured output that can be validated, parsed, and stored | [`structured-output/lead-qualification-schema.md`](structured-output/lead-qualification-schema.md) |

## Recommended learning path

```text
simple support prompt
   ↓
prompt audit
   ↓
improved prompt
   ↓
prompt test cases
   ↓
reusable workflow
```

## What to look for

When reviewing the examples, pay attention to whether the prompt defines:

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

If one of these is missing, the prompt may still work in a demo, but fail in a real workflow.

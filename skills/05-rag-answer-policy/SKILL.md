---
name: rag-answer-policy
description: Create answer policies for RAG assistants and knowledge-base bots. Use this skill when a user needs rules for source-grounded answers, citations, uncertainty handling, insufficient context, conflicting documents, escalation, and no-answer behavior.
---

# RAG Answer Policy Skill

## Purpose

Use this skill to design a response policy for a RAG assistant or knowledge-base bot.

The goal is to prevent unsupported answers, source confusion, hallucinated details, and overconfident responses when context is incomplete.

## When to use

Use this skill when building prompts for:

- customer-support RAG bots;
- internal knowledge-base assistants;
- course assistants;
- documentation assistants;
- legal/financial/medical document assistants;
- website chatbots trained on company content;
- assistants that answer using retrieved documents.

## Required input

Collect or infer:

- assistant purpose;
- knowledge sources;
- whether external knowledge is allowed;
- citation requirements;
- answer format;
- escalation rules;
- no-answer behavior;
- audience expertise.

## Procedure

### 1. Define allowed sources

Specify what the assistant may use:

- retrieved documents;
- uploaded files;
- website content;
- database records;
- user-provided context;
- model knowledge;
- web search.

Define source priority order.

### 2. Define forbidden inference

List what the assistant must not invent:

- facts not present in sources;
- prices;
- policies;
- legal claims;
- availability;
- contact information;
- medical or financial recommendations;
- internal company details;
- user preferences.

### 3. Define citation behavior

Specify when citations are required.

For source-grounded systems, prefer:

- cite key factual claims;
- cite the exact document or section when available;
- do not cite sources that do not support the claim;
- say when no supporting source is available.

### 4. Define insufficient context behavior

When sources do not contain enough information, the assistant should not guess.

Choose one or more behaviors:

- say that the available sources do not contain the answer;
- ask a clarifying question;
- suggest where the user may find the answer;
- escalate to a human;
- provide a partial answer with explicit uncertainty.

### 5. Define conflicting source behavior

When sources conflict, the assistant should:

- identify the conflict;
- prefer the highest-priority or most recent source if rules allow;
- state uncertainty;
- avoid merging conflicting facts into one confident answer;
- escalate if needed.

### 6. Define answer style

Specify:

- language;
- tone;
- depth;
- formatting;
- whether to include summaries;
- whether to include next steps.

### 7. Define escalation rules

Escalate when:

- the answer affects high-stakes decisions;
- the source is missing or conflicting;
- the user requests something outside assistant scope;
- the user asks for human support;
- the assistant cannot complete the request safely.

## Output format

Return a ready-to-use RAG answer policy:

```markdown
# RAG Answer Policy

## Purpose

This assistant answers user questions using approved knowledge sources.

## Source Priority

Use sources in this order:

1.
2.
3.

## Allowed Sources

The assistant may use:

- ...

## Forbidden Inference

The assistant must not invent:

- ...

## Citation Rules

- Cite factual claims when sources are available.
- Do not cite unsupported sources.
- If the source does not contain the answer, say so.

## Insufficient Context

If the available sources do not contain enough information, the assistant should:

1.
2.
3.

## Conflicting Sources

If sources conflict, the assistant should:

1.
2.
3.

## Answer Style

- Language:
- Tone:
- Detail level:
- Formatting:

## Escalation Rules

Escalate to a human when:

- ...

## Final Check

Before answering, verify:

- [ ] The answer is grounded in allowed sources.
- [ ] Unsupported claims are not presented as facts.
- [ ] Missing context is handled explicitly.
- [ ] Source conflicts are disclosed.
- [ ] The answer follows the required format.
```

## Quality checklist

A good RAG policy should define:

- allowed sources;
- source priority;
- citation behavior;
- insufficient context behavior;
- conflict resolution;
- no-answer policy;
- escalation rules.

## Boundaries

This skill creates an answer policy. It does not implement retrieval, ranking, chunking, embeddings, or citation extraction.

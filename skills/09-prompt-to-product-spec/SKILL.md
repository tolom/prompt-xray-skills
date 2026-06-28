---
name: prompt-to-product-spec
description: Convert an AI prompt, assistant idea, or rough automation concept into a practical product specification with MVP scope, user stories, data sources, integrations, workflows, admin controls, and acceptance criteria.
---

# Prompt to Product Spec Skill

## Purpose

Use this skill to turn a prompt or AI assistant idea into a product specification.

The goal is to move from "the model should do this" to "the product should support this workflow".

A prompt is often only one part of an AI product. Real products also need data, UI, integrations, permissions, monitoring, and fallback behavior.

## When to use

Use this skill when the user has:

- an AI assistant idea;
- a prompt that should become a product feature;
- a chatbot concept;
- an automation workflow;
- a client request;
- a demo idea;
- a prototype that needs MVP definition;
- a prompt that should be implemented by a developer or coding agent.

## Required input

Collect or infer:

- target users;
- business goal;
- current manual workflow;
- model task;
- data sources;
- expected outputs;
- channels or UI;
- integrations;
- admin needs;
- constraints;
- MVP deadline or budget if available.

If some details are missing, mark assumptions clearly.

## Procedure

### 1. Extract the product goal

State the product goal in one sentence.

```text
The product should help [user] achieve [business outcome] by using AI to [workflow].
```

### 2. Identify users and roles

Define:

- end user;
- admin/operator;
- customer/client;
- developer/maintainer;
- AI assistant role.

### 3. Define current workflow

Describe how the task is done manually today.

This helps identify what should and should not be automated.

### 4. Define AI responsibilities

Specify what the model should do:

- understand requests;
- extract data;
- classify cases;
- generate drafts;
- answer from sources;
- recommend next actions;
- prepare reports;
- trigger workflows.

### 5. Define human responsibilities

Specify what humans still approve or handle:

- final decisions;
- sensitive replies;
- payments;
- legal review;
- account changes;
- exceptions;
- quality control.

### 6. Define data sources

List:

- user input;
- files;
- CRM;
- website;
- database;
- email;
- chat history;
- knowledge base;
- third-party APIs.

### 7. Define UX/channel

Specify where the feature lives:

- web app;
- Telegram bot;
- website widget;
- admin panel;
- email workflow;
- CRM extension;
- internal dashboard;
- API only.

### 8. Define MVP scope

Separate:

- must-have;
- should-have;
- later;
- explicitly out of scope.

### 9. Define acceptance criteria

For each core feature, define how to know it is done.

### 10. Define risks and open questions

List:

- technical risks;
- product risks;
- data risks;
- UX risks;
- prompt/model risks;
- unanswered questions.

## Output format

Return the spec as:

```markdown
# Product Specification

## One-Sentence Product Goal

The product should...

## Users and Roles

| Role | Description | Main Needs |
|---|---|---|

## Current Manual Workflow

1.
2.
3.

## Proposed AI Workflow

1.
2.
3.
4.

## AI Responsibilities

- ...

## Human Responsibilities

- ...

## Data Sources

| Source | Required | Notes |
|---|---:|---|

## User Experience

- Channel:
- Main screens/messages:
- Admin controls:

## MVP Scope

### Must-have

- ...

### Should-have

- ...

### Later

- ...

### Out of scope

- ...

## Integrations

- ...

## Acceptance Criteria

- [ ] ...
- [ ] ...
- [ ] ...

## Risks

| Risk | Impact | Mitigation |
|---|---|---|

## Open Questions

- ...

## Suggested Build Plan

1.
2.
3.
```

## Quality checklist

A good product spec should:

- define the business outcome;
- separate AI and human responsibilities;
- define MVP boundaries;
- include data sources;
- include acceptance criteria;
- identify risks;
- be actionable for implementation.

## Boundaries

This skill creates a product specification. It does not estimate budget, timeline, or implementation complexity unless the required project details are available.

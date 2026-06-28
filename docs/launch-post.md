# Launch Post Draft

## Short version

Stop shipping fragile prompts. X-Ray them first.

I started building **Prompt X-Ray Skills** — a set of reusable `SKILL.md` workflows for writing, auditing, testing, and hardening LLM prompts before they become part of real products, agents, automations, RAG systems, support bots, or coding workflows.

Most prompt engineering resources focus on tips, tricks, and example prompts.

This project treats a prompt as a behavioral specification for an AI system.

The workflow is simple:

```text
weak prompt -> X-Ray audit -> improved prompt -> test cases -> reusable workflow
```

The first version includes skills for:

- turning vague ideas into prompt briefs;
- auditing weak prompts;
- designing system prompts;
- writing agent instructions;
- creating RAG answer policies;
- designing structured outputs;
- generating prompt quality checks;
- debugging bad model responses;
- turning AI assistant ideas into product specs.

The goal is not to make prompts longer.

The goal is to make prompts more reliable.

Repository: https://github.com/tolom/prompt-xray-skills

## Longer version

I keep seeing the same problem in AI projects:

People do not really have a prompt problem.

They have a specification problem.

The prompt is vague. The source of truth is missing. The output format is not defined. The model is expected to guess missing business context. There are no test cases. Then everyone is surprised when the AI behaves inconsistently.

So I started building **Prompt X-Ray Skills**.

It is a small open collection of reusable `SKILL.md` workflows for writing, auditing, testing, and hardening LLM prompts.

The idea is simple:

> A prompt is a behavioral specification for an AI system.

Good prompts should define:

- goal;
- context;
- role;
- inputs;
- constraints;
- source of truth;
- output format;
- uncertainty behavior;
- quality criteria;
- test cases.

A weak prompt usually looks harmless:

```text
You are a helpful support assistant. Answer customer questions professionally and provide useful information. If you don't know something, be honest.
```

But it hides several production risks:

- the assistant's scope is undefined;
- the source of truth is missing;
- "professionally" and "useful" are vague;
- no escalation behavior is defined;
- no output format is defined;
- no rule exists for missing or conflicting information;
- there are no test cases.

Prompt X-Ray turns that into a structured workflow:

```text
Mission
Source of Truth
Scope
Workflow
Style
Output Format
Missing Information Behavior
Escalation Rules
Test Cases
```

The first version includes:

- Prompt Brief Builder
- Prompt Auditor
- System Prompt Architect
- Agent Instruction Writer
- RAG Answer Policy
- Structured Output Designer
- Prompt Test Generator
- Prompt Debugger
- Prompt to Product Spec

This is not a prompt marketplace.

This is not a list of magic phrases.

It is a practical toolkit for people who use LLMs in real workflows and want more reliable behavior.

Repository: https://github.com/tolom/prompt-xray-skills

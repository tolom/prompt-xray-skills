# Launch Post Draft

## Short version

Your prompt is not bad.

It is underspecified.

I started building **Prompt X-Ray Skills** — a small open `SKILL.md` workflow pack for people building real AI systems: assistants, support bots, RAG apps, coding agents, automations, structured-output pipelines, and internal AI tools.

Most prompt resources give you examples.

Prompt X-Ray treats a prompt as a behavioral specification for an AI system.

The workflow is simple:

```text
weak prompt -> X-Ray audit -> improved prompt -> test cases -> reusable workflow
```

The first version includes skills for:

- turning vague ideas into prompt briefs;
- auditing weak prompts;
- designing system prompts;
- writing coding-agent instructions;
- creating RAG answer policies;
- designing structured outputs;
- generating prompt quality checks;
- debugging bad model responses;
- turning AI assistant ideas into product specs.

The goal is not to make prompts longer.

The goal is to make prompt behavior more reliable.

Repository: https://github.com/tolom/prompt-xray-skills

## Longer version

I keep seeing the same failure pattern in AI projects:

The demo works.

Then the prompt gets reused in a real workflow and starts failing in predictable ways:

- the assistant answers outside its scope;
- the source of truth is unclear;
- the output format changes randomly;
- the model guesses missing business context;
- RAG answers include unsupported claims;
- coding agents make broad changes from vague instructions;
- nobody has test cases for the prompt.

The problem is usually not that the prompt is "bad".

The problem is that the prompt is underspecified.

So I started building **Prompt X-Ray Skills**.

It is a small open collection of reusable `SKILL.md` workflows for auditing, rewriting, testing, and hardening prompts before they become part of real products.

The core idea:

> A prompt is a behavioral specification for an AI system.

A production prompt should usually define:

- goal;
- context;
- role;
- inputs;
- constraints;
- source of truth;
- decision rules;
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
- there are no pass/fail cases.

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

It is a prompt reliability toolkit for people who use LLMs in real workflows and want behavior they can explain, reuse, and test.

Repository: https://github.com/tolom/prompt-xray-skills

## Reddit / Hacker News style version

I built a small open toolkit for a problem I keep seeing in AI projects: prompts are treated like text snippets, but in production they behave more like underspecified software specs.

A vague prompt may work in a demo, then fail when it has to handle missing context, source-of-truth conflicts, structured output, escalation, RAG citations, or coding-agent scope control.

Prompt X-Ray Skills is a `SKILL.md` workflow pack for auditing, rewriting, testing, and hardening prompts.

The workflow:

```text
weak prompt -> audit -> improved prompt -> test cases -> reusable workflow
```

It includes workflows for system prompts, coding-agent instructions, RAG answer policies, structured outputs, prompt debugging, test generation, and turning assistant ideas into product specs.

The premise is simple: a prompt is a behavioral specification for an AI system. If it cannot be tested, it is not production-ready.

Repo: https://github.com/tolom/prompt-xray-skills

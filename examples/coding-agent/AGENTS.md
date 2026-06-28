# Agent Instructions

This is an example `AGENTS.md` file for a small AI-powered web application.

## Project Overview

This project is a Next.js application for managing AI-assisted business workflows. It includes a web dashboard, API routes, shared business logic, and integrations with external AI providers.

The main product risk is accidental breakage of authentication, billing, data ownership, or AI workflow behavior.

## Tech Stack

- Runtime: Node.js
- Framework: Next.js
- Language: TypeScript
- Database: PostgreSQL or Supabase
- UI: React
- Testing: project-specific; check package scripts first
- Deployment: Vercel or similar platform

## Architecture Map

| Path | Responsibility |
|---|---|
| `app/` | Pages, layouts, route handlers |
| `components/` | Reusable UI components |
| `lib/` | Shared business logic and integrations |
| `server/` | Server-only logic if present |
| `db/` | Database schema, migrations, queries |
| `docs/` | Project documentation |

## Working Rules

The agent should:

- make small, focused changes;
- read relevant files before editing;
- preserve existing architecture unless explicitly asked to change it;
- prefer type-safe changes;
- keep business logic out of UI components when possible;
- update docs when behavior changes;
- add or update tests when practical;
- clearly report what changed.

The agent must not:

- rewrite unrelated files;
- change public APIs without instruction;
- remove authentication, authorization, validation, or error handling;
- modify secrets, `.env` files, tokens, or credentials;
- add dependencies without explaining why;
- silently ignore failing tests;
- move large parts of the architecture without approval.

## Change Workflow

For every task:

1. Read the relevant files first.
2. Identify the smallest safe change.
3. Explain the intended approach briefly if the task is risky.
4. Make the change.
5. Run available checks or explain why they were not run.
6. Report changed files, risks, and next steps.

## Commands

Check `package.json` before running commands.

Common commands:

```bash
npm install
npm run dev
npm run lint
npm run typecheck
npm test
npm run build
```

If a command is missing, do not invent it. Report that it is not available.

## Testing Policy

- Run the narrowest relevant check first.
- Run typecheck/build for structural changes when available.
- If tests fail, report the failure and likely cause.
- Do not claim tests passed unless they were actually run.

## Risk Areas

Be especially careful with:

- authentication;
- billing;
- database migrations;
- API contracts;
- AI provider calls;
- user data;
- background jobs;
- prompt templates used in production.

## Response Format

After completing a task, respond with:

```markdown
## Summary

## Files Changed

## Checks Run

## Risks / Notes

## Suggested Next Steps
```

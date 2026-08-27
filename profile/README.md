<p align="center">
  <img src="https://github.com/organizations/bot-flow/settings/profile" alt="Bot Flow icon" width="180" />
</p>

<h1 align="center">Bot Flow</h1>

<p align="center">
  A workflow engine framework for building configurable business processes for AI chatbots.
</p>

## Overview

Bot Flow is a workflow engine framework designed for AI chatbots. It defines
business processes through stable, fixed paradigms while allowing users to
configure the process itself.

This focus distinguishes Bot Flow from frameworks such as LangChain. LangChain
primarily provides building blocks for composing models, tools, retrieval, and
agent behavior. Bot Flow operates at the business-process layer: it determines
which steps are available, how they transition, what data they require, and
which rules must be enforced throughout a conversation.

The two approaches can be complementary. A Bot Flow workflow may invoke a
LangChain chain or agent as one implementation step while retaining control of
the overall business process.

## Why Bot Flow?

- **Business-first workflows** — model real user journeys instead of only
  connecting AI components.
- **Fixed execution paradigms** — keep critical transitions and rules explicit
  and predictable.
- **User-configurable processes** — let users compose and adjust workflows
  without rewriting the engine.
- **AI-framework independence** — integrate models, tools, agents, or external
  services behind workflow steps.
- **Operational visibility** — provide an admin interface for future workflow
  configuration, execution monitoring, and management.

## Bot Flow and LangChain

| Concern | Bot Flow | LangChain |
| --- | --- | --- |
| Primary abstraction | Business workflow | Model, tool, retrieval, and agent composition |
| Main audience | Workflow designers and business users | AI application developers |
| Core responsibility | Process steps, transitions, rules, and state | AI calls, tool execution, retrieval, and agent behavior |
| Configuration goal | User-configurable business processes | Developer-configured AI application logic |
| Relationship | Can orchestrate AI capabilities as workflow steps | Can implement AI-powered steps inside a Bot Flow workflow |

## Architecture

The repository currently provides the foundation for two layers:

- `backend/` — FastAPI service with versioned routes, CORS, OpenAPI
  documentation, health checks, and tests.
- `frontend/` — Next.js 16 admin interface based on
  [NextAdminHQ/nextjs-admin-dashboard](https://github.com/NextAdminHQ/nextjs-admin-dashboard).

The dashboard overview already calls the FastAPI endpoint at
`GET /api/v1/dashboard/overview`. The remaining template widgets use local mock
data and can be connected as workflow engine capabilities are introduced.

## Project Status

Bot Flow is in its initial foundation stage. The FastAPI backend and admin
frontend are operational; the workflow definition schema, execution engine,
runtime state management, and visual workflow configuration are planned next.

## Requirements

- Python 3.11+
- Node.js 20+
- npm 10+

## Quick Start

Install the backend and frontend dependencies:

```bash
make backend-install
make frontend-install
cp backend/.env.example backend/.env
cp frontend/.env.example frontend/.env.local
```

Start the backend and frontend in separate terminals:

```bash
make backend-dev
make frontend-dev
```

Local services:

- Admin UI: http://localhost:3000
- API documentation: http://localhost:8000/docs
- Health check: http://localhost:8000/api/v1/health

## Verification

```bash
make backend-test
make frontend-lint
make frontend-build
```

## Roadmap

- Define a versioned workflow schema.
- Implement deterministic workflow execution and transition rules.
- Add runtime state, persistence, retries, and execution history.
- Build a visual workflow editor in the admin interface.
- Provide chatbot adapters and AI-framework integration points.

## Upstream Attribution

The frontend began from the free NextAdmin dashboard template downloaded from
the upstream `main` branch on 2026-08-27. Its original README and project agent
guidelines remain in `frontend/`.

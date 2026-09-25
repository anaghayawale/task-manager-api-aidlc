# Application Design

## Architecture Decision

The first release is a modular monolith: one TypeScript/Express application deployed as Vercel serverless functions. It is divided into routing, identity, authorization, validation/operations, workspace, task, persistence, and audit modules. Firebase Authentication and MongoDB Atlas remain external managed services.

## Design Summary

- Top-level task endpoints receive an explicit `workspaceId`; services authorize membership before all workspace reads or mutations.
- Firebase token verification occurs server-side in a dedicated adapter.
- Workspace Service owns membership use cases; Task Service owns task CRUD and derived due-date behavior.
- Repositories isolate MongoDB driver access.
- Audit Service persists append-only task and membership events and emits safe structured logs.
- Operational Middleware supplies rate limits, restrictive CORS, validation, safe errors, logging, timeouts, and health endpoints.
- API documentation is delivered as Markdown for the first release.

## Deferred Detail

Functional Design will define exact schema constraints, status-transition rules, date semantics, filter behavior, authorization edge cases, and testable properties. NFR and Infrastructure Design will define concrete providers, settings, monitoring, retention, CI checks, and deployment configuration.

## Artifact Index

- `components.md`: Component boundaries and responsibilities.
- `component-methods.md`: High-level TypeScript interfaces.
- `services.md`: Request and service orchestration.
- `component-dependency.md`: Dependency matrix and data flow.

## Extension Compliance Summary

| Extension / Rule Group | Status | Rationale |
|---|---|---|
| Security Baseline | Compliant | The design implements separation of concerns, defense in depth, server-side access control, auditability, validation, and safe failure boundaries. |
| Resiliency Baseline | N/A | Disabled in state tracking. |
| Partial Property-Based Testing | N/A | PBT property identification is deferred to Functional Design. |

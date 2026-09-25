# Components

## API Router

**Purpose**: Exposes health, workspace, membership, and top-level task endpoints.

**Responsibilities**: Route requests, apply middleware, map HTTP requests/responses, and publish Markdown API documentation.

**Interface**: Receives HTTP requests and delegates to application services; does not contain domain rules.

## Identity Adapter

**Purpose**: Verifies Firebase bearer tokens and exposes the authenticated principal.

**Responsibilities**: Extract bearer credentials, verify Firebase ID tokens, validate issuer/audience/expiry, and create an authenticated request context.

**Interface**: `verifyRequest(request): AuthenticatedPrincipal`.

## Authorization Policy

**Purpose**: Enforces owner and member permissions at workspace and task boundaries.

**Responsibilities**: Confirm workspace membership, enforce owner-only membership management, and deny unauthorized access by default.

**Interface**: Accepts a principal, workspace identifier, and required permission; returns authorization success or a denial.

## Validation and Error Middleware

**Purpose**: Validates untrusted input and produces safe, consistent API errors.

**Responsibilities**: Apply schema validation and body-size limits; sanitize/reject unsafe fields; assign correlation IDs; map errors without exposing internals.

**Interface**: HTTP middleware plus request-schema validation helpers.

## Workspace Service

**Purpose**: Orchestrates workspace and membership use cases.

**Responsibilities**: Create or resolve workspaces, add/remove members, and invoke authorization and audit recording.

**Interface**: Receives authenticated requests from the router and delegates persistence to repositories.

## Task Service

**Purpose**: Orchestrates task CRUD, filtering, pagination, due-date behavior, and audit recording.

**Responsibilities**: Authorize workspace access; validate task commands; invoke repositories; calculate derived overdue information for responses.

**Interface**: Receives task commands and queries from the router and returns application DTOs.

## MongoDB Repositories

**Purpose**: Persist workspace, membership, task, and audit-event records in MongoDB Atlas.

**Responsibilities**: Use typed, parameterized driver operations; enforce collection access boundaries; use TLS-configured MongoDB connections.

**Interface**: Repository methods expose domain persistence operations and do not expose raw database access to routers.

## Audit Service

**Purpose**: Records security-relevant task and membership changes.

**Responsibilities**: Write append-only audit events to MongoDB and emit structured logs without secrets or Firebase tokens.

**Interface**: Accepts an audit command containing actor, action, resource, timestamp, and permitted before/after values.

## Operational Middleware

**Purpose**: Applies cross-cutting runtime protections and operational behavior.

**Responsibilities**: Rate limiting, restrictive CORS, security headers where applicable, structured logging, shallow/deep health checks, dependency timeouts, and global failure handling.

**Interface**: Express middleware and health handlers composed at the API entrypoint.

## Extension Compliance Summary

| Extension / Rule Group | Status | Rationale |
|---|---|---|
| Security Baseline | Compliant | Dedicated identity, authorization, validation, audit, and operational components provide separation of concerns and defense in depth. |
| Resiliency Baseline | N/A | Disabled in state tracking. |
| Partial Property-Based Testing | N/A | Components do not yet define implementation-level properties. |

# Services

## Request Processing Flow

1. API Router receives a request.
2. Validation and Operational Middleware assign correlation context, enforce limits, apply safe headers/CORS/rate limits, and validate input.
3. Identity Adapter verifies the Firebase token for protected endpoints.
4. The relevant application service invokes Authorization Policy before reading or changing workspace data.
5. Workspace Service or Task Service uses MongoDB Repositories to perform persistence.
6. A mutating use case calls Audit Service to persist an audit event and emit a structured log.
7. API Router maps the result or safe error to an HTTP response.

## Workspace Service Orchestration

Workspace Service coordinates owner-only membership changes:

- Require an authenticated principal.
- Require the caller to be workspace owner.
- Change membership through the repository.
- Record the mutation through Audit Service.

## Task Service Orchestration

Task Service coordinates shared task behavior:

- Require an authenticated principal and workspace membership.
- Validate command/query data before persistence.
- Create, retrieve, list, update, or delete tasks through the task repository.
- Produce derived due-date/overdue response data.
- Record every successful mutation through Audit Service.

## Operational Service Responsibilities

Operational Middleware coordinates non-domain concerns at the API boundary. Health checks may query MongoDB with an explicit timeout; all other database and Firebase calls have bounded timeouts and fail closed.

## Extension Compliance Summary

| Extension / Rule Group | Status | Rationale |
|---|---|---|
| Security Baseline | Compliant | Service orchestration layers validation, authentication, authorization, persistence isolation, and audit logging. |
| Resiliency Baseline | N/A | Disabled in state tracking. |
| Partial Property-Based Testing | N/A | No test implementation is produced in this artifact. |

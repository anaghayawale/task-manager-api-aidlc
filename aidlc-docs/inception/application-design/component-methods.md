# Component Methods

The signatures below describe high-level interfaces. Detailed validation and business rules are deferred to Functional Design.

```typescript
type AuthenticatedPrincipal = { firebaseUid: string; email?: string };
type WorkspaceRole = "owner" | "member";
type TaskStatus = "todo" | "in-progress" | "completed";
type TaskPriority = "low" | "medium" | "high";

interface IdentityAdapter {
  verifyRequest(authorizationHeader: string | undefined): Promise<AuthenticatedPrincipal>;
}

interface AuthorizationPolicy {
  requireMembership(principal: AuthenticatedPrincipal, workspaceId: string): Promise<void>;
  requireOwner(principal: AuthenticatedPrincipal, workspaceId: string): Promise<void>;
}

interface WorkspaceService {
  addMember(principal: AuthenticatedPrincipal, workspaceId: string, memberUid: string): Promise<void>;
  removeMember(principal: AuthenticatedPrincipal, workspaceId: string, memberUid: string): Promise<void>;
}

interface TaskService {
  createTask(principal: AuthenticatedPrincipal, input: CreateTaskInput): Promise<TaskView>;
  getTask(principal: AuthenticatedPrincipal, taskId: string): Promise<TaskView>;
  listTasks(principal: AuthenticatedPrincipal, query: ListTasksQuery): Promise<PagedTaskView>;
  updateTask(principal: AuthenticatedPrincipal, taskId: string, input: UpdateTaskInput): Promise<TaskView>;
  deleteTask(principal: AuthenticatedPrincipal, taskId: string): Promise<void>;
}

interface AuditService {
  record(event: AuditEventInput): Promise<void>;
}
```

### Input and Output Boundaries

- `CreateTaskInput` and `UpdateTaskInput` include `workspaceId` as required request data for the selected top-level route style.
- `ListTasksQuery` includes `workspaceId`, pagination, and optional status, priority, and due-date filters.
- `TaskView` returns safe task fields, timestamps, and derived overdue status; it never returns credentials or internal persistence fields.
- Repository interfaces are internal implementation details and are not exposed as public API contracts.

## Extension Compliance Summary

| Extension / Rule Group | Status | Rationale |
|---|---|---|
| Security Baseline | Compliant | Interfaces make identity verification and authorization explicit before service operations. |
| Resiliency Baseline | N/A | Disabled in state tracking. |
| Partial Property-Based Testing | N/A | Detailed property identification occurs in Functional Design. |

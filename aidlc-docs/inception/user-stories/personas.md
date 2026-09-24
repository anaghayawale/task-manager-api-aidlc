# Personas

## Workspace Owner

- **Goal**: Establish a shared workspace and control who can collaborate in it.
- **Permissions**: Manage membership and, as a member, manage workspace tasks.
- **Needs**: Clear membership outcomes, reliable task visibility, and confidence that other workspaces remain isolated.
- **Primary stories**: US-01, US-02, US-03, US-04, US-05, US-06.

## Workspace Member

- **Goal**: Create, find, prioritize, and complete shared-workspace tasks with other members.
- **Permissions**: Create, read, update, and delete tasks in workspaces they belong to.
- **Needs**: An accurate task lifecycle, useful due-date and priority filters, and immediate feedback when an action is not allowed.
- **Primary stories**: US-03, US-04, US-05, US-06.

## API Client Developer

- **Goal**: Integrate a client application with a predictable, secure REST API.
- **Permissions**: Uses Firebase-issued tokens on behalf of authenticated users; does not receive elevated server-side privileges.
- **Needs**: Stable request and response contracts, documented validation behavior, pagination, and safe error responses.
- **Primary stories**: US-07.

## Persona-to-Story Map

| Persona | Relevant Stories |
|---|---|
| Workspace Owner | US-01 through US-06 |
| Workspace Member | US-03 through US-06 |
| API Client Developer | US-07 |

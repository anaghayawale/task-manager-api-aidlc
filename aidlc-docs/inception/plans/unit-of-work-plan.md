# Unit of Work Plan

## Proposed Decomposition

The application remains one deployable modular monolith. The proposed logical units are:

1. **Foundation and Identity**: serverless entrypoint, configuration, Firebase verification, validation, safe errors, health checks, logging, and middleware.
2. **Workspace and Task Domain**: MongoDB persistence, workspace membership, authorization policy, task CRUD, task query behavior, and audit events.
3. **Quality and Delivery**: Jest/fast-check tests, Vercel configuration, security controls, Markdown API documentation, dependency scanning, and SBOM generation.

## Execution Checklist

- [x] Review requirements, stories, application design, and execution plan.
- [x] Identify logical implementation boundaries while preserving one deployable application.
- [x] Identify initial dependency sequence: foundation before domain, then quality/delivery verification.
- [x] Collect and validate the unit-decomposition answers below.
- [ ] Obtain explicit approval of this unit-of-work plan.
- [ ] Generate unit-of-work.md with unit definitions, responsibilities, and code organization strategy.
- [ ] Generate unit-of-work-dependency.md with dependency matrix and sequence.
- [ ] Generate unit-of-work-story-map.md mapping every story to one or more units.
- [ ] Validate unit boundaries, dependencies, and story assignments.
- [ ] Update this plan, workflow state, and audit trail.
- [ ] Present generated units for explicit approval.

## Questions

## Question 1
How should implementation work be grouped within the single deployable modular monolith?

A) Use the three logical units proposed above: foundation/identity, workspace/task domain, and quality/delivery (recommended)

B) Use one complete API unit with modules implemented together

X) Other (please describe after [Answer]: tag below)

[Answer]: A

## Question 2
How should the units be sequenced?

A) Sequential: foundation/identity, then workspace/task domain, then quality/delivery (recommended)

B) Build foundation/identity first, then work on domain and quality/delivery in parallel

X) Other (please describe after [Answer]: tag below)

[Answer]: Can we take authentication at last and keep the workspace and task one first 

## Question 3
How should source code be organized in this greenfield project?

A) Feature modules under `src/` with shared middleware and infrastructure folders, one `api/` Vercel entrypoint, and colocated/unit test folders (recommended)

B) Layered folders under `src/` for routes, services, repositories, middleware, and models

X) Other (please describe after [Answer]: tag below)

[Answer]: B

## Question 4
Who owns coordination across the logical units?

A) One implementation owner coordinates all units sequentially (recommended for this project)

B) Separate owners may work on the domain and quality/delivery units after the foundation is ready

X) Other (please describe after [Answer]: tag below)

[Answer]: A

## Extension Compliance Summary

| Extension / Rule Group | Status | Rationale |
|---|---|---|
| Security Baseline | Compliant | Foundation and domain units isolate security-sensitive controls and include quality verification. |
| Resiliency Baseline | N/A | Disabled in state tracking. |
| Partial Property-Based Testing | Compliant | Quality and Delivery explicitly owns the selected partial PBT work. |

## Confirmed Decomposition Decisions

- Use the three proposed logical units.
- Sequence work security-first: Foundation and Identity, then Workspace and Task Domain, then Quality and Delivery.
- Use layered source folders for routes, services, repositories, middleware, and models.
- One implementation owner coordinates units sequentially.

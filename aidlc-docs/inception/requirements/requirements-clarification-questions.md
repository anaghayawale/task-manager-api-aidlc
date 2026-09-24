# Task Management API Requirements Clarifications

Your earlier answers establish a Node.js/TypeScript direction, external authentication, shared workspaces, Vercel deployment intent, and enabled security/resiliency controls. Please answer every question below by filling in its `[Answer]:` value.

## Question 1
Which database choice and connection model should be documented?

A) Node.js, TypeScript, Express, and MongoDB Atlas using a private connection string stored in Vercel environment variables

B) Node.js, TypeScript, Express, and PostgreSQL using a managed cloud database connection stored in Vercel environment variables

X) Other (please describe after [Answer]: tag below)

[Answer]: A

## Question 2
Which external identity provider will authenticate API users?

A) Clerk

B) Auth0

C) Firebase Authentication

X) Other (please describe after [Answer]: tag below)

[Answer]: which one's setup is easy and wont cost us anything

## Question 3
Which shared-workspace role model should the API enforce?

A) Owner and member: owners manage workspace membership; members create and manage only their own tasks

B) Owner, editor, and viewer: owners manage membership; editors can manage all workspace tasks; viewers have read-only access

C) Owner and member: all members can create, read, update, and delete any task in their workspace

X) Other (please describe after [Answer]: tag below)

[Answer]: C

## Question 4
How should the API be deployed on Vercel?

A) Vercel serverless functions, with MongoDB Atlas and the identity provider managed externally

B) Vercel serverless functions for preview/testing only; production hosting will be selected later

X) Other (please describe after [Answer]: tag below)

[Answer]: A

## Question 5
What availability and recovery goal is appropriate for this workload?

A) RPO/RTO measured in hours: backup and restore; lowest cost; suitable for a non-critical workload

B) RPO/RTO in tens of minutes: pilot light; infrastructure and data prepared for recovery

C) RPO/RTO in minutes: warm standby; reduced-capacity service ready to scale up

D) Near-real-time RPO/RTO: multi-site active/active

E) Single-region deployment is acceptable; no cross-region disaster recovery is needed

X) Other (please describe after [Answer]: tag below)

[Answer]: E

## Question 6
How should production changes be governed?

A) Use an existing organizational change-management process (describe it after the answer)

B) No formal process exists; propose a lightweight change record, approval, and rollback-note process

C) Formal change management is not required for this workload

X) Other (please describe after [Answer]: tag below)

[Answer]: C

## Question 7
Which CI/CD tooling and deployment process should be used?

A) GitHub Actions to test and deploy to Vercel

B) Vercel's Git integration for deployments, with no separate CI pipeline initially

X) Other (please describe after [Answer]: tag below)

[Answer]: B

## Question 8
How should a failed production deployment be rolled back?

A) Redeploy the previous version-pinned Vercel deployment

B) Use an existing organizational rollback procedure (describe it after the answer)

X) Other (please describe after [Answer]: tag below)

[Answer]: No action to be taken for this

## Question 9
What deployment strategy is acceptable?

A) Direct deployment, appropriate for a non-critical workload

B) Canary release with progressive traffic shifting and automated rollback

X) Other (please describe after [Answer]: tag below)

[Answer]: A

## Question 10
How should production incidents be handled?

A) Use an existing incident-response process (describe it after the answer)

B) No formal process exists; propose a lightweight incident response and post-incident review process

C) Formal incident response is not required for this workload

X) Other (please describe after [Answer]: tag below)

[Answer]: C

## Question 11
Which test tooling should be used for TypeScript, including the selected partial property-based testing enforcement?

A) Vitest for example-based tests and fast-check for property-based tests

B) Jest for example-based tests and fast-check for property-based tests

X) Other (please describe after [Answer]: tag below)

[Answer]: B

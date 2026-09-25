# Unit of Work Sequencing Clarification

Authentication and authorization must be complete before any API endpoint is runnable because the Security Baseline is enabled. Select a sequencing option that preserves this requirement.

## Question 1
How should the three logical units be sequenced?

A) Build the workspace/task domain models, repositories, and pure services first; then add the foundation/identity boundary before exposing API routes; finish with quality/delivery (recommended)

B) Build all workspace/task behavior first; then build foundation/identity and wire it into every endpoint before testing or deployment; finish with quality/delivery

C) Use the original security-first sequence: foundation/identity, then workspace/task domain, then quality/delivery

X) Other (please describe after [Answer]: tag below)

[Answer]: C

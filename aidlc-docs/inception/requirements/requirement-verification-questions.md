# Task Management API Requirements Questions

Please answer every question by replacing the corresponding `[Answer]:` value. Choose `X` and add a brief explanation when the listed choices do not fit.

## Question 1
Which technology stack should the API use?

A) Node.js, TypeScript, Express, and PostgreSQL

B) Python, FastAPI, and PostgreSQL

C) Java, Spring Boot, and PostgreSQL

X) Other (please describe after [Answer]: tag below)

[Answer]: Node.js, TypeScript, Express, and MongoDB since creating an instance would be easy their

## Question 2
What authentication approach should the API provide?

A) Email and password registration/login with JWT bearer access tokens

B) Email and password registration/login with server-side sessions

C) External identity provider only (for example, OAuth or OpenID Connect)

X) Other (please describe after [Answer]: tag below)

[Answer]: C

## Question 3
Who can access and modify a task?

A) Only the authenticated user who created the task

B) Task owners plus explicitly assigned users

C) Shared team workspace with role-based access

X) Other (please describe after [Answer]: tag below)

[Answer]:  C

## Question 4
Which task fields and lifecycle are required beyond title, priority, and due date?

A) Description and status: todo, in-progress, completed

B) Description, status, tags, and completion timestamp

C) Title, description, status, priority, due date, recurrence, and tags

X) Other (please describe after [Answer]: tag below)

[Answer]: A

## Question 5
What priority model should apply?

A) Low, medium, high

B) Low, medium, high, urgent

C) Numeric priority from 1 through 5

X) Other (please describe after [Answer]: tag below)

[Answer]: A

## Question 6
How should the task collection endpoint support retrieval?

A) Return the caller's tasks with pagination only

B) Pagination plus filters for status, priority, and due date

C) Pagination, filters, and sortable fields

X) Other (please describe after [Answer]: tag below)

[Answer]: B

## Question 7
What delivery target and operational expectations apply to this first version?

A) Local development only, with Docker optional

B) Containerized service prepared for cloud deployment

C) Production deployment target must be designed now

X) Other (please describe after [Answer]: tag below)

[Answer]: I'm planning to deploy this on vercel as of now. So you can select which option would be good here

## Question 8
Should the Security Baseline extension be enforced as blocking constraints?

A) Yes, enforce all security rules

B) No, skip the security rules

X) Other (please describe after [Answer]: tag below)

[Answer]: A

## Question 9
Should the Resiliency Baseline be applied as directional design-time guidance?

A) Yes, apply the resiliency baseline

B) No, skip the resiliency baseline

X) Other (please describe after [Answer]: tag below)

[Answer]: A

## Question 10
Should Property-Based Testing rules be enforced?

A) Yes, enforce all property-based testing rules

B) Partial, enforce them for pure functions and serialization round-trips

C) No, skip property-based testing rules

X) Other (please describe after [Answer]: tag below)

[Answer]: B

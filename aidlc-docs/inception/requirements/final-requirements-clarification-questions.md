# Final Requirements Clarifications

Two decisions remain before the requirements can be finalized. The selected Security and Resiliency Baselines make a rollback mechanism mandatory.

## Question 1
Which external identity provider should be used?

Recommendation: Firebase Authentication is the simplest no-cost option for this project. Firebase documents a no-cost Spark plan and describes Firebase Authentication as a complete backend sign-in solution. Do not select phone authentication if avoiding billing-account requirements is important.

A) Firebase Authentication (recommended for a low-cost Vercel and MongoDB Atlas project)

B) Clerk

C) Auth0

X) Other (please describe after [Answer]: tag below)

[Answer]: A

## Question 2
Which rollback mechanism should be documented for a failed production deployment?

“No action” is not permitted because the enabled Resiliency Baseline requires an explicit rollback choice.

A) Redeploy the previous version-pinned Vercel deployment

B) Use an existing organizational rollback procedure (describe it after the answer)

X) Other (please describe after [Answer]: tag below)

[Answer]: let's skip  Resiliency Baseline  then


7 design principles of well-architected applications
-------------
- speedy, simple, singular
- share nothing
- assume no hardware affinity (hardware agnostic way)
- use events to trigger transactions (get comfortable with async operations)
- think of concurrent requests, not total requests
- orchestrate your application with state machines, not functions (don't call functions from other functions)
- design for failures and duplicates

idempotency - making sure that no matter how many times you run a piece of code, send a request, etc. that the result is always the same 

most important related to idempotency is design for failures and duplicates, impossible w/o idempotency

source:
https://docs.aws.amazon.com/wellarchitected/latest/serverless-applications-lens/general-design-rinciples.html
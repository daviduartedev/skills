# Implement

Load when dispatching one ticket whose blockers are done.

The ticket is implemented only inside the dispatched context, on this session's model. The prompt contains:

- ticket id, title, acceptance criteria, and the spec issue
- branch `feat/<slug>`, and the instruction to stay on it
- the seams from the spec: a failing test first, then the code that passes it, when the repo has a test runner
- the instruction to run the repo's typecheck
- the instruction to review this ticket's diff against the ticket and the repo's documented standards
- the consumer's documented orientation step before reading code, when the repo has one (a knowledge-graph query, `CONTEXT.md`, ADRs in the area)
- one commit on `feat/<slug>` for this ticket
- the instruction to stop after that commit

The dispatched context does not push, amend, or take another ticket.

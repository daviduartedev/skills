---
name: esteira
description: "Use when a message lists several small adjustments to land together on one feature branch."
---

# esteira

A batch of small adjustments on one `feat/<slug>` branch. This window holds scope, the branch, shared understanding, the spec, and the tickets. Each ticket is implemented in a fresh context. This window then runs the published security check and the delivery gate.

A large module, a greenfield effort, or a single obvious change is outside this skill. Stop and say so.

## Process

1. **Scope.** The adjustments are the ones in the message. Choose a short kebab-case slug from that scope, with no issue numbers.

2. **Branch.** Update the consumer's default branch and its integration branch from the remote when the repo has both (often `main` and `develop`); otherwise update the default branch. Create `feat/<slug>` from the integration branch, or from the default branch when there is no integration branch. If the working tree holds a different piece of work, stop. If `feat/<slug>` already exists and it is this scope, use it.

3. **Shared understanding.** Load [shared understanding](references/shared-understanding.md). Done when the user has confirmed it.

4. **Spec.** The spec is not final. Run [security-design-review](../security-design-review/SKILL.md) for this slug. Confirm the test seams with the user. Load [spec](references/spec.md) and publish it on the consumer's issue tracker. Use the glossary in the consumer's `CONTEXT.md` when that file exists.

5. **Tickets.** Load [tickets](references/tickets.md). Each ticket is one tracer bullet that fits in one fresh context. Done when the user has approved the breakdown and the tickets are published, blockers first, with their blocking edges.

6. **Implement.** Take the frontier: every ticket whose blockers are done. Finish one ticket before starting the next. For each ticket, dispatch a subagent in a new context on this session's model. Load [implement](references/implement.md) for the prompt. If this harness cannot dispatch a subagent, stop and say so.

7. **Verify the diff.** When every ticket has its own commit, run [security-review](../security-review/SKILL.md) against the merge-base of `feat/<slug>` and the branch it was cut from.

8. **Drive.** Run [dvd-tests](../dvd-tests/SKILL.md) on `feat/<slug>`. That run does not commit.

## Output

Primary: the conversation, as each step finishes:

1. The scope list and the slug
2. The branch name
3. The confirmed understanding
4. The spec issue URL and the path `docs/security/<feature-slug>.md`
5. The ticket list with blocking edges
6. One commit per ticket
7. The `security-review` report
8. E2E results, then the unchecked checklist

`SR-*` findings stay in the report. This run does not open fix tickets. Push and a pull request wait until the human confirms the checklist.

## Completion criteria

The run is done when all of the following hold:

- Scope is a list of small adjustments and the slug is chosen, or the run stopped because the job is a large module, greenfield work, or a single change
- The working tree is on `feat/<slug>` cut from the updated base branch, or the run stopped because the tree held other work
- The user has confirmed the shared understanding
- The spec issue is published with the ready label named in the spec reference, and `docs/security/<feature-slug>.md` exists
- The user approved the breakdown; tickets are published, blockers first, each with its blocking edges
- Every ticket has its own commit on `feat/<slug>`
- `security-review` has reported on that branch
- E2E results and the unchecked checklist are in the conversation
- Nothing has been pushed

# esteira

Human guide to the batch skill in this collection. Agent instructions live in `skills/esteira/`. This page is for the engineer who decides when to run it and what to do with the result.

The name is the assembly line: one batch, one branch, tickets in order. Invoke as **esteira** (`/esteira`).

## What it does

The skill takes several small adjustments from the message and walks them through one `feat/<slug>` branch:

1. Agree what the batch is, and cut the branch from an updated base
2. Reach a shared understanding with you
3. Run **security-design-review**, then publish the spec
4. Break the spec into tracer-bullet tickets after you approve the breakdown
5. Implement each ticket in a fresh context, one commit per ticket
6. Run **security-review** on the branch
7. Run **dvd-tests** (browser Drive, E2E results, unchecked checklist)

It reaches those three skills. It does not restate them.

## When to run it

The message is a list of small adjustments that belong on one branch.

Skip it for a large module, a greenfield effort, or a single obvious change. The agent stops and says so.

You can type the name. The agent can also reach it when the message matches that slot.

## Input

- The adjustments in the message
- The consumer repository, including `CONTEXT.md` and issue-tracker docs when they exist
- Your answers during the shared-understanding rounds, and your approval of the test seams and the ticket breakdown

## Output

In the conversation, as the work proceeds: the scope and slug, the branch, the confirmed understanding, the spec issue and `docs/security/<feature-slug>.md`, the tickets, one commit per ticket, the security-review report, then the dvd-tests E2E results and the unchecked checklist.

You work the checklist. Push and a pull request wait for that confirmation.

Ticket commits happen during implement. The dvd-tests run still does not commit. Security findings stay in the report; this run does not open fix tickets.

## Non-goals

- A specify/implement platform for arbitrary work
- A second copy of the AppSec reviews or the delivery gate
- A push or a pull request before you confirm the checklist

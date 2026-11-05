---
name: grill-to-ship
description: "Use when a grill has settled its decisions and the work should run spec, tickets, prototype approval, one implement commit per ticket, then dvd-tests."
disable-model-invocation: true
---

# grill-to-ship

Run at the end of a grill. The settled decisions in this conversation are the input. Carry them through five stages, in order, each behind a human gate. Every decision is already made: this run synthesises and builds, it does not re-interview.

**Thin** is the leading word for every stage: one decision per spec story, one behaviour per ticket, one ticket per commit. A thin piece is easy to check and hard to get wrong.

## Loading a stage skill

Each stage runs another skill. Invoke it with the Skill tool when it is model-invocable. When it is user-invoked only (`disable-model-invocation: true`), read its `SKILL.md` from the consumer's skill folders (`.claude/skills/<name>/`, then `.agents/skills/<name>/`) and follow it as written. When neither exists, stop and name the missing skill.

## Process

1. **Ground.** State the base branch and the working branch the grill settled; create the branch from the base when it does not exist. List every settled decision and every open question with its provisional decision, numbered as the grill numbered them. Done when the human has the list and the branch exists.

2. **Spec** with `to-spec`. Write one user story per settled decision; an item that carries several decisions gets several stories. Open questions go under Further Notes with their provisional decision. Done when the spec issue is published and the human has confirmed the test seams.

3. **Tickets** with `to-tickets`. Cut thin: one observable behaviour per ticket, sized to land as one commit. Wide renames follow that skill's expand–contract rule. Mark each ticket that changes a screen as **UI**. Done when the human approved the breakdown and every ticket is published with its blocking edges.

4. **Build, ticket by ticket**, on the frontier (tickets whose blockers are done):
   1. A **UI** ticket first goes through `prototype` (the UI branch). Show the variants and wait. Done when the human named the approved variant; fold that verdict into the ticket.
   2. Then `implement` the ticket. Done when its tests and typecheck pass and exactly one commit, naming the ticket, sits on the working branch.
   3. Report the commit in one line and take the next frontier ticket.

5. **Deliver** with `dvd-tests` once every ticket has its commit. Done when its E2E results and unchecked manual list are printed.

Stop there. Pushing and opening a pull request wait for the human's request.

## Rules

- A gate is passed only by the human's own message in this conversation.
- A finding that contradicts a settled decision goes to the human as a question; the decision stands until they answer.
- A failing test outside the ticket's scope is reported, not fixed, unless the human asks.

## Completion criteria

The run is done when all of the following hold:

- Every settled decision maps to at least one spec story, and every open question sits in the spec with its provisional decision
- Every ticket is published, and every UI ticket carries the variant the human approved
- Every ticket has exactly one commit on the working branch, or is reported as blocked with the reason
- `dvd-tests` output is printed, and nothing was pushed or opened as a pull request without a request

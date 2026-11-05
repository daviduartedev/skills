# grill-to-ship

Human guide to the delivery runner in this collection. Agent instructions live in `skills/grill-to-ship/`. This page is for the engineer who decides when to run it and what each gate asks of them.

Invoke as **grill-to-ship** (`/grill-to-ship`). It is user-invoked only: the agent never starts it on its own.

## What it does

At the end of a grill, it carries the settled decisions through five stages, each one thin (one decision per story, one behaviour per ticket, one ticket per commit):

1. **Ground**: lists the settled decisions and open questions, and creates the working branch
2. **Spec**: runs `to-spec` and publishes the spec issue
3. **Tickets**: runs `to-tickets` and publishes thin tickets, marking the ones that change a screen
4. **Build**: for each ticket, a `prototype` of the screen first when it is a UI ticket, then `implement` with one commit
5. **Deliver**: runs `dvd-tests`

## When to run it

Right after a grill ends with every branch answered. Run it in the same conversation, so the decisions are already in context.

Skip it for a one-line fix, or when the grill left decisions open that block the work.

## Your gates

The run waits for you at each of these:

- Confirm the test seams of the spec
- Approve the ticket breakdown
- Pick the prototype variant of each screen
- Work the `dvd-tests` checklist

A finding that contradicts a decision comes back to you as a question.

## Requirements

The consumer repository needs `to-spec`, `to-tickets`, `prototype`, `implement`, and `dvd-tests` installed, plus a configured issue tracker. User-invoked stage skills are read from `.claude/skills/` or `.agents/skills/` and followed as written.

## Non-goals

- Re-opening the grill or re-asking settled decisions
- Pushing or opening a pull request without your request
- Fixing failing tests outside the ticket in hand

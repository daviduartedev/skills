# A batch lane for small adjustments

The published GitHub repo is `daviduartedev/skills`. [ADR-0001](0001-personal-skills-collection.md) kept a general specify/implement platform out and left further skills to a spec. A batch of small adjustments still needs one place that cuts the branch, holds the conversation through the spec and the tickets, and reaches the skills this collection already publishes.

**esteira** is that lane, and this note is its spec. Shared understanding, the spec, the tickets, and the per-ticket hand-off are written in this collection's words. `security-design-review` runs before the spec is published. `security-review` runs after the ticket commits, against the merge-base of `feat/<slug>` and the branch it was cut from. `dvd-tests` runs last and still does not commit. Push waits until the human confirms the checklist.

Ticket commits land during implement so each ticket has a commit of its own. That is the lane's unit of done. It does not change the rule that the delivery run itself does not commit.

Outside the lane: a large module, greenfield work, a single obvious change, scanners, and a general specify/implement platform.

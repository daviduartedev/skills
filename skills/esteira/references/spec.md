# Spec

Load when shared understanding is confirmed, `security-design-review` has written `docs/security/<feature-slug>.md`, and the test seams have been confirmed with the user.

Publish one issue on the consumer's tracker. Read `docs/agents/issue-tracker.md` in the consumer repo when it exists. When the tracker vocabulary is undocumented, ask where to publish before creating the issue.

Title: the slug, in words. Label `ready-for-agent` when the tracker uses that label. When `docs/agents/triage-labels.md` maps that role to another string, use the mapped string.

Body, in this order, omitting an empty section:

- **Problem.** The user's situation.
- **Behaviour.** What changes for the user.
- **Decisions.** Choices already confirmed. No file paths.
- **Seams.** The public boundaries to test. The ones the user just confirmed.
- **Security.** The `SEC-*` ids from `docs/security/<feature-slug>.md`. Ids only.
- **Out of scope.** What this batch leaves alone.

Vocabulary follows the consumer's `CONTEXT.md` when that file exists.

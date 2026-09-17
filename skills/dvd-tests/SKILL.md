---
name: dvd-tests
description: "Use when a completed implementation needs a local run, browser E2E against that app, and a human-observable smoke checklist before commits."
---

# dvd-tests

After a completed implementation: **Drive** the live UI in a browser, **Verify** with returned E2E results, **Deliver** an **unchecked** human checklist. Stop before commits. Wait for the human.

Former name: `smoke-test-list`.

## Process

1. Establish the implementation branch: the branch the user named; otherwise a `feat/<slug>` recorded in cycle `request.md`; otherwise the current branch when it already holds that work. Stop if the working tree is on a different piece of work.

2. Resolve how to run the app, in this order: this conversation (_window_); cycle `request.md` then the smoke section of `plan.md`; the consumer's documented dev script. Load [local run](references/local-run.md) for free-port, reuse, and credential rules. If those sources show no local UI, skip the start and the Drive step, and say so.

3. Start on a free port. Print the URL. Wait until the process is ready (a ready log, or a successful fetch). Leave a healthy server on this branch running.

4. **Drive.** When a local UI is up, load [playwright](references/playwright.md) and exercise the happy path (and the relevant negative check) against that URL, using login profiles and copy from the _window_ then the cycle sources. Return pass / fail / blocked per check. Do not author a committed test file unless the _window_ asked for one.

5. **Deliver.** Build one unchecked checklist of observable checks. Sources in that order: the _window_; `request.md` (locked copy, roles, what is out of scope); `plan.md` smoke section; observable scenarios; then user-visible tasks. Include one relevant negative check. Named login profiles only when those sources state them; ask if a role is required and none is recorded.

6. Print both blocks in the conversation: E2E results, then the manual list. One line after them: the human works the list, then confirms before any commit.

## Output

Primary: the conversation, in this order:

1. E2E results (each automatable check: pass, fail, or blocked, with what was seen)
2. The manual checklist (title, URL, login profiles when documented, path through the UI, unchecked items)

This run does not commit, open a pull request, write a validation file, or tick the human list.

## Completion criteria

The run is done when all of the following hold:

- Implementation branch established, or the run stopped because the working tree was other work
- Local URL printed, or the run states there is no local UI to start
- E2E results printed, or the Drive step skipped because there is no local UI
- Every manual checklist item is something a human can see or do; none is ticked
- Documented login profiles included when the sources named them; otherwise none invented
- Conversation states that commits wait for the human

# dvd-tests

Human guide to the delivery skill in this collection. Agent instructions live in `skills/dvd-tests/`. This page is for the engineer who decides when to run it and what to do with the result.

Former name: `smoke-test-list`. Invoke as **dvd-tests** (`/dvd-tests`).

## What it does

The skill walks an agent through a **Drive / Verify / Deliver** check of a completed implementation:

1. Start the app locally on a free port when a UI exists
2. **Drive** that UI in a browser (E2E) using the conversation (_window_) and cycle docs
3. **Verify** by printing pass / fail / blocked for each automatable check
4. **Deliver** an unchecked list of things you can see or do

It does not mark the work validated, and it does not commit.

## When to run it

After implement, before you treat the change as done. The agent can notice that slot from the skill description. You can also invoke it by name.

Skip it when there is nothing new to look at, or when you are still in design or AppSec review (`security-design-review`, `security-review`).

## Input

Whatever already exists for the change:

- This conversation: URL, login, product, what is out of scope
- The implementation branch
- Cycle docs when present (`request.md`, `plan.md` smoke, observable scenarios, user-visible tasks)
- How to start the app, if a local UI exists

Login profiles come from those sources or from you. The skill will not invent them.

## Output

Two conversation blocks:

1. E2E results (what the agent saw in the browser)
2. The manual list: title, local URL, documented logins, path through the UI, unchecked observable items, including a relevant negative check

You work the list. When it holds, you ask for commits in a later message. That confirmation is yours; this skill never commits.

## Non-goals

- Implementation, AppSec review, or opening a pull request
- Tick-boxes on the human list filled in by the agent
- A second validation file beside your own process
- Hard-coded ports, packages, or demo passwords for a particular product
- A committed Playwright spec unless you asked for one

# Capture

Load when taking the screenshots.

## Driver

Prefer the local UI already up from `dvd-tests` (same branch, printed URL). If none is running, start it the way that skill would: window, then cycle docs, then the consumer's documented dev script. Do not invent a port or a login.

Drive with the consumer's browser CLI when one exists (`playwright-cli` or equivalent). One screenshot per observable check, not a full-page dump of every route.

## Resolution and crop

- Native **1x**. Do not resize with PIL or similar; that introduces artefacts.
- Control display width later in the PR description (`<img width="360">` / `600`), not in the file.
- Before/after pairs: same viewport width and the same crop. Otherwise the comparison is meaningless.
- Name files so a human can match them while dragging: `01-ad-mobile-mockup.png`, not `screenshot.png`.

## Where to write files

Write **outside** the git worktree that will be pushed, for example:

- `$TMPDIR/pr-screenshots-<slug>/` (or `%TEMP%\pr-screenshots-<slug>\` on Windows)
- A consumer evidence folder the window already named, if and only if that folder is gitignored and is not on the feature branch

Print the absolute path. If a file lands inside the consumer repo by mistake, delete it from the index and the tree before any commit. Do not leave it untracked hoping someone notices.

## What to shoot

Sources, in that order: the window; the linked issue's acceptance criteria; `dvd-tests` E2E checks that passed. Include one relevant negative when the ticket has one (for example a surface that must stay unchanged).

# pr-screenshots

Human guide to the delivery skill that puts UI evidence in a pull request. Agent instructions live in `skills/pr-screenshots/`. This page is for the engineer who decides when to run it and what to do with the files.

Invoke as **pr-screenshots** (`/pr-screenshots`).

## What it does

The skill walks an agent through capturing native screenshots of a visible change and drafting the evidence section of the GitHub PR description. The image files stay on disk outside the branch. You drag them into the description in the GitHub UI.

It does not commit those files, and it does not add an `assets/` folder to the pull request.

## When to run it

After `dvd-tests` (you have confirmed the UI) and when opening or filling a pull request that changes layout, styling, or other on-screen behaviour.

Skip it when the diff is not something a reviewer can see (backend-only, docs).

## Input

Whatever already exists for the change:

- The implementation branch and its local URL
- The linked issue's acceptance criteria, when present
- The `dvd-tests` E2E list, when that run already happened

## Output

1. A folder of PNG/JPEG files (absolute path in the conversation)
2. A filename + caption list
3. Markdown for the PR evidence section, with empty `src` waiting for your drop

You open the PR on GitHub and drop each file onto the matching caption. GitHub stores those uploads on `user-images.githubusercontent.com`, which is what actually renders on a private repo.

## Non-goals

- Committing screenshots to `assets/`, `pr-assets/`, `docs/pr-evidence/`, or an orphan branch
- Pasting `raw.githubusercontent.com` links for a private repository
- Opening the PR unless a sibling skill in the same session already does
- Replacing `dvd-tests` (that skill still drives the UI and waits for you before commits)

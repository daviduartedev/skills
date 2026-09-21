# pr-screenshots

Human guide to the delivery skill that puts UI evidence in a pull request. Agent instructions live in `skills/pr-screenshots/`. This page is for the engineer who decides when to run it and what to do with the files.

Invoke as **pr-screenshots** (`/pr-screenshots`).

## What it does

The skill walks an agent through capturing native screenshots of a visible change and putting them in the GitHub PR description. The agent uploads each file to GitHub (`user-attachments`) and writes those URLs into the description. The files stay off the implementation branch.

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
3. The PR description, with each image pointing at `github.com/user-attachments/assets/…`

Refresh the pull request while logged in. On a private repository those URLs 404 if fetched without a session; they render for anyone who can open the PR.

## Non-goals

- Committing screenshots to `assets/`, `pr-assets/`, `docs/pr-evidence/`, or an orphan branch
- Pasting `raw.githubusercontent.com` links for a private repository
- Opening the PR unless a sibling skill in the same session already does
- Replacing `dvd-tests` (that skill still drives the UI and waits for you before commits)

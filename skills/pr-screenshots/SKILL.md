---
name: pr-screenshots
description: "Use when a pull request changes something visible and reviewers need those screenshots in the PR description, not committed as assets on the branch."
---

# pr-screenshots

After a visible change is ready for review: **Capture** native screenshots of what a person can see, **Caption** each one against the ticket, **Place** them only in the pull request description. Never add an `assets/` folder (or any screenshot path) to the implementation PR.

Sits after `dvd-tests` (human has confirmed the UI) and next to opening the PR. Inspired by [github/awesome-copilot pr-screenshots](https://github.com/github/awesome-copilot); this collection's rule is GitHub-only and forbids committing the images.

## Process

1. Confirm the diff shows something a reviewer can see (layout, styling, UI, charts, CLI output). Stop with one line when it does not.

2. **Capture.** Load [capture](references/capture.md). Shoot the after state on the implementation branch's local UI. Shoot before only when that state is still on the machine (do not reconstruct it by reverting the branch). Map each file to a ticket acceptance criterion when an issue exists.

3. Save files **outside the consumer working tree** that will be pushed. Print the absolute folder and the filename list. Never `git add` those files. Never create `assets/`, `pr-assets/`, `docs/pr-evidence/`, or an orphan branch of screenshots on the consumer repository.

4. **Caption** and **Place.** Load [github-description](references/github-description.md). Draft the evidence section; images live only in the GitHub PR description. After the PR exists, list each local filename with its caption and ask the human to drag those files into the description in the GitHub UI, matching by name.

5. Print the filename list in the conversation. Stop. The human drops the files; this skill does not commit.

## Output

Primary: the conversation, then the PR description evidence section.

1. Absolute folder of the PNG/JPEG files
2. A table or list: filename, caption, ticket criterion when one exists
3. The markdown block for **Evidências** / Evidence, with image alts filled and `src` left for the human drop (or already filled if they pasted)

This run does not commit, force-push, or open a pull request unless a sibling PR skill in the same session already owns that step — and even then it still does not add image files to the diff.

## Completion criteria

The run is done when all of the following hold:

- The change is visible, or the run stopped because it is not
- Screenshots exist on disk outside the pushed working tree
- No screenshot path is staged, committed, or present in the PR diff
- The PR description draft names every file and what to notice
- The human has been asked to drop the files into the GitHub description, matching by filename
- The conversation states that the implementation branch stays free of an `assets/` (or equivalent) screenshot folder

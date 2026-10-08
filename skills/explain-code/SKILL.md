---
name: explain-code
description: "Use when the human needs how a module is implemented in this repo — seams, call path, and what the tests lock."
---

# explain-code

Read-only orientation of a **module** as code in the consumer repository. Ground in the files and tests that exist. Leave product rules to `explain-product` and hosting to `explain-infra`.

## Process

1. Resolve the module from the _window_, then the current branch or spec title, then one question. Stop until a module is named.

2. Load [seams](references/seams.md). Read the public entry points, the tests that lock them, and the product docs only to name a mismatch.

3. Print the narrative from [narrative](references/narrative.md) in the conversation language. Cite `path:line` for every behavioural claim.

## Output

The conversation. No file in the consumer repo unless the _window_ asked for one.

## Completion criteria

The run is done when all of the following hold:

- A module is named
- Every behavioural claim cites `path:line`
- Tests that lock the module are named, or one line that none exist
- A mismatch between code and product docs is stated when both exist and disagree
- Nothing in the run required mutating the workspace

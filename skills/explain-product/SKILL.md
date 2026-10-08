---
name: explain-product
description: "Use when the human lacks product domain for a module, or asks what the docs already decide versus what is still open."
---

# explain-product

Read-only orientation of a **module** in the consumer product. Ground in the docs that already exist. Separate **decided** rules from **open** questions. Leave implementation and hosting to `explain-code` and `explain-infra`.

## Process

1. Resolve the module from the _window_, then the current branch or spec title, then one question. Stop until a module is named.

2. Load [sources](references/sources.md). Read every source that exists for that module. Cite a path for every claim. Mark a gap as **open** when no source decides it.

3. Print the narrative from [narrative](references/narrative.md) in the conversation language.

## Output

The conversation. No file in the consumer repo unless the _window_ asked for one.

## Completion criteria

The run is done when all of the following hold:

- A module is named
- Every **decided** line cites a source that exists
- Every **open** line is something no named source settles
- How the module connects to neighbouring product language is stated, or one line that the sources do not connect it yet
- Nothing in the run required mutating the workspace

---
name: explain-infra
description: "Use when the human needs how this product is hosted, deployed, or run locally."
---

# explain-infra

Read-only orientation of **where the consumer product runs**. Ground in compose files, deploy workflows, cycle infra notes, and env **names**. Leave product rules to `explain-product` and application seams to `explain-code`.

## Process

1. Resolve the environment from the _window_ (local, staging, production), then one question if several exist and the ask is ambiguous.

2. Load [surfaces](references/surfaces.md). Read every surface that exists. Print **names** of secrets and parameters; leave values unread in the conversation.

3. Print the narrative from [narrative](references/narrative.md) in the conversation language.

## Output

The conversation. No file in the consumer repo unless the _window_ asked for one.

## Completion criteria

The run is done when all of the following hold:

- The environment in scope is named
- How to reach the app in that environment is stated from a source, or marked **open**
- Secret and parameter **names** are listed without their values
- Local run is described only when a documented script or compose file exists
- Nothing in the run required mutating the workspace

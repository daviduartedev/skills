# Sources

Load this file in step 2 of `explain-product`. Walk the list in order. Skip a path that is absent. Do not invent a rule to fill a skip.

1. The _window_ (names, constraints, and out-of-scope already stated)
2. Consumer `CONTEXT.md` (glossary)
3. Consumer `docs/adr/` that mention the module
4. Consumer `spec/features/<module>/` (readme, issue files, open questions)
5. GitHub issues for that module (`gh`), including parent specs still open
6. Cycle `request.md` / `plan.md` when the module has a cycle folder
7. Consumer maps: `docs/FIGMA_MAP.md`, `docs/SPEC_MAP.md`, cronograma pages, user guide
8. Figma node ids already recorded in those docs (names and intent; skip pixel implementation)

A later source that contradicts an earlier one is reported as a conflict, not silently preferred.

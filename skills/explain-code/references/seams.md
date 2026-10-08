# Seams

Load this file in step 2 of `explain-code`. Follow the public boundary, not private helpers.

1. HTTP or UI entry for the module (controller, route, page)
2. The service or module that owns the rule
3. Persistence only as the store the service uses (table or file), not an ER lecture
4. Tests at that same boundary (`*.spec.ts`, `*.test.tsx`)
5. `CONTEXT.md` / spec only when checking whether the code still matches the product language

Skip generated lockfiles and vendored code. Skip rewriting the module.

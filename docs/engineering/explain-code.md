# explain-code

Human guide to the code-orientation skill in this collection. Agent instructions live in `skills/explain-code/`. This page is for the engineer who decides when to run it and what to do with the result.

Invoke as **explain-code** (`/explain-code`).

## What it does

The skill follows a **module** from its public entry (route, controller, page) through the owning service to the store, and names the tests that lock that boundary. It cites `path:line`. When product docs disagree with the code, it states the mismatch.

It does not change the code.

## When to run it

When you need how this repo implements a module. The agent can notice that slot from the skill description. You can also invoke it by name.

Skip it when you want product decisions (`explain-product`) or hosting (`explain-infra`).

## Input

- A **module**
- The consumer repository on disk (and tests at the public seam)

## Output

A conversation narrative: call path, seams, what the tests lock, mismatch with product docs when both exist.

## Non-goals

- Product glossary lectures (that is `explain-product`)
- Deploy topology (that is `explain-infra`)
- A refactor or a patch

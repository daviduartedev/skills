# explain-product

Human guide to the product-orientation skill in this collection. Agent instructions live in `skills/explain-product/`. This page is for the engineer who decides when to run it and what to do with the result.

Invoke as **explain-product** (`/explain-product`).

## What it does

The skill walks an agent through the consumer repo's **existing product docs** for one module: glossary, ADRs, specs, issues, cycle notes, Figma maps. It prints what those sources already **decide**, what they leave **open**, and how the module connects to neighbouring product language.

It does not implement, review security, or invent a scoring rule to fill a gap.

## When to run it

When you lack domain for a module, or when you need a split between mapped decisions and open questions before writing a spec or ticket. The agent can notice that slot from the skill description. You can also invoke it by name.

Skip it when you want call paths (`explain-code`) or hosting (`explain-infra`).

## Input

- A **module** (you name it, or the conversation / branch already points at one)
- Whatever already exists: `CONTEXT.md`, `docs/adr/`, `spec/features/<module>/`, GitHub issues, cycle `request.md`, maps

## Output

A conversation narrative: what it is, how it connects, decided, open, out of scope, sources read. Each decided line cites a path or issue. No consumer file unless you asked for one.

## Non-goals

- Implementation, AppSec review, or `dvd-tests`
- Filling open questions with a guessed formula
- Teaching the framework (`explain-code`) or the deploy path (`explain-infra`)

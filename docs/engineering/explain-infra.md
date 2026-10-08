# explain-infra

Human guide to the infra-orientation skill in this collection. Agent instructions live in `skills/explain-infra/`. This page is for the engineer who decides when to run it and what to do with the result.

Invoke as **explain-infra** (`/explain-infra`).

## What it does

The skill reads compose files, deploy workflows, cycle infra notes, and env **names** to say how the consumer product is hosted, deployed, or run locally. Secret **values** stay out of the conversation.

It does not open a tunnel, rotate credentials, or change infrastructure.

## When to run it

When you need local ports, staging versus production hosts, or the deploy path. The agent can notice that slot from the skill description. You can also invoke it by name.

Skip it when you want product rules (`explain-product`) or application seams (`explain-code`).

## Input

- An **environment** when more than one exists (local, staging, production)
- Documented surfaces: compose, workflows, cycle infra notes, `.env.example`

## Output

A conversation narrative: environments, how it runs, data stores by name, secret names, open gaps.

## Non-goals

- Pasting live passwords or connection strings
- Guessing AWS topology when the session is expired
- Product or code orientation

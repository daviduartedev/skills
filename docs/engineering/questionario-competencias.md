# questionario-competencias

Human guide to the locked record of the IKOA competency questionnaire. Agent instructions live in `skills/questionario-competencias/`. This page is for the engineer who decides when to run it.

Invoke as **questionario-competencias** (`/questionario-competencias`).

## What it does

The skill holds the closed rules for Questionário A: who answers, when the Meu mapa seal is granted once, how the five-segment bar is derived from the mean, and which lines are still open. The formula and the seal table live only in the skill.

## When to run it

When a change touches the questionnaire, the average bar, the Meu mapa seal, or Meu desenvolvimento. The agent can notice that slot from the skill description. You can also invoke it by name.

Skip it for a general product read (`explain-product`) or for trail work, which stays off `feat/questionario-a`.

## Output

A change that still matches the skill, or an edit to the skill when you close an open line.

## Non-goals

- Inventing a recommendation engine, an age gate, or a second payment for the same `sourceKey`
- Copying trail commits onto the questionnaire branch

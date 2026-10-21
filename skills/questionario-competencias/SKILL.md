---
name: questionario-competencias
description: "Use when changing the IKOA Questionário de competências, its average bar, the Meu mapa seal, or Meu desenvolvimento."
---

# questionario-competencias

Locked product record for the IKOA competency questionnaire on branch `feat/questionario-a`. Apply it before changing that module. Trail work stays off this branch.

## Process

1. Treat **Decided** and **Result** as the rules already closed.
2. Leave each **Open** line open until the human closes it in this file.
3. Keep a second completion of questionnaire id `competencias` from adding another 30 pontos.

## Decided

Questionário A, version 1.0 of 20/07/2026. Thirty-five statements, five in each competency, in the fixed competency order. Ids `s1`–`s35`. Ids and text of `s1`–`s5` stay, so stored answers survive. The only questionnaire id is `competencias`.

Only an `aluno` answers, and only an `aluno` opens `/questionario` and `/questionario/desenvolvimento`. While the questionnaire is pending, Home shows the reminder card. `professor`, `admin_escola`, and `responsavel` stay out. The age and year-group gate (10–13, 5º–8º) stays unimplemented.

Completion is every statement answered. The seal is granted on the transition from pending to completed.

| Who | Slug | `sourceKey` | Pontos |
|---|---|---|---|
| Aluno | `meu-mapa-de-competencias` | `questionnaire:competencias` | 30, once |
| Professor of the class | `professor-mapa-de-competencias` | `questionnaire:competencias` | null |

The professor seal is granted when half the enrolled students in that class have completed. Earn uniqueness is aluno + slug + `sourceKey`, with duplicates skipped. Ranking sums earn rows. The average does not enter Ranking. A null `pontos` adds nothing.

The student seal is visible in the student gallery, the ficha, and the guardian view: grey until earned, full colour after. The professor map seal, both trail seals, and Portfólio stay hidden.

Meu desenvolvimento is an accordion. The first competency starts open. **Ver respostas** opens one competency and closes the previous. **Ver respostas** and the chosen answer use `--ikoa-primary`. The statement text stays muted.

## Result

Option points: Nunca `0`, Às vezes `1`, Muitas vezes `2`, Sempre `3`, Não sei responder `0`.

The level of a competency is the mean of its answered statements. No answers means `0`. The five-segment bar uses `0` when the mean is `0` or less, otherwise `min(5, round((mean / 3) * 5))`. Mean `3` fills every segment. The same bar is on the conclusion and on Meu desenvolvimento. The seal is the flat 30 above, not this mean.

## Open

- The Home card says the questionnaire brings personalised recommendations. No recommendation is produced from the mean.
- Delivery is unfinished: the accordion, the purple answer text, and the visible student seal are uncommitted on `feat/questionario-a`; the branch is not pushed; issue 556 on `orbe-soft/orbe-development-board` is open.
- A different `sourceKey` for the same slug still adds another 30. Production rows were not read. The `main` that is published still hides the screen and still uses the five-statement catalogue. Finishing the thirty-five later reuses `questionnaire:competencias`, so that key does not pay twice.

## Completion criteria

The run is done when all of the following hold:

- The diff keeps every **Decided** rule and the **Result** formula
- Questionnaire id `competencias` still grants the student seal once
- Each **Open** line is unchanged, or the human closed it by editing this file
- Trail changes are absent from `feat/questionario-a`

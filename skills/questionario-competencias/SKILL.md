---
name: questionario-competencias
description: "Use when changing the IKOA Questionário de competências, its average bar, the Meu mapa seal, Meu desenvolvimento, or the school switch in Configurações."
---

# questionario-competencias

Locked product record for the IKOA competency questionnaire on branch `feat/questionario-a`. Apply it before changing that module. Trail work stays off this branch.

## Process

1. Treat **Decided** and **Result** as the rules already closed.
2. Leave each **Open** line open until the human closes it in this file.
3. Keep a second completion of questionnaire id `competencias` from adding another 30 pontos.

## Decided

Questionário A, version 1.0 of 20/07/2026. Thirty-five statements, five in each competency, in the fixed competency order. Ids `s1`–`s35`. Ids and text of `s1`–`s5` stay, so stored answers survive. The only questionnaire id is `competencias`.

Only an `aluno` answers, and only an `aluno` opens `/questionario` and `/questionario/desenvolvimento`. `professor`, `admin_escola`, and `responsavel` stay out of that flow. The age and year-group gate (10–13, 5º–8º) stays unimplemented.

`questionnaireEnabled` defaults to off on the school. Only `admin_escola` turns **Questionário de competências** on in Configurações. While it is off, reading and answering are refused, Home shows no reminder, `/questionario` returns to Home, and the student seal stays out of the gallery. While it is on, a pending `aluno` sees the reminder card and the introduction opens, and the seal returns. Pontos already summed in Ranking stay when the switch turns off.

Completion is every statement answered. The seal is granted on the transition from pending to completed.

| Who | Slug | `sourceKey` | Pontos |
|---|---|---|---|
| Aluno | `meu-mapa-de-competencias` | `questionnaire:competencias` | 30, once |
| Professor of the class | `professor-mapa-de-competencias` | `questionnaire:competencias` | null |

The professor seal is granted when half the enrolled students in that class have completed. Earn uniqueness is aluno + slug + `sourceKey`, with duplicates skipped. Ranking sums earn rows. The average does not enter Ranking. A null `pontos` adds nothing.

While the switch is on, the student seal is visible in the student gallery, the ficha, and the guardian view: grey until earned, full colour after. While it is off, that seal stays out of those lists. The professor map seal, both trail seals, and Portfólio stay hidden from the student gallery. The professor's own **Mapa de competências dos alunos** stays on the professor list after the switch turns off.

Meu desenvolvimento is an accordion. The first competency starts open. **Ver respostas** opens one competency and closes the previous. **Ver respostas** and the chosen answer use `--ikoa-primary`. The statement text stays muted.

## Result

Option points: Nunca `0`, Às vezes `1`, Muitas vezes `2`, Sempre `3`, Não sei responder `0`.

The level of a competency is the mean of its answered statements. No answers means `0`. The five-segment bar uses `0` when the mean is `0` or less, otherwise `min(5, round((mean / 3) * 5))`. Mean `3` fills every segment. The same bar is on the conclusion and on Meu desenvolvimento. The seal is the flat 30 above, not this mean.

## Open

- The Home card says the questionnaire brings personalised recommendations, and the introduction says the platform can suggest trails and projects. No recommendation is produced from the mean.
- A different `sourceKey` for the same slug still adds another 30. The key `questionnaire:competencias` does not pay twice. Production rows were not read; an unread production database is not evidence of empty tables. Published `main` still hides the screen and still uses the five-statement catalogue. Merging the thirty-five reuses `questionnaire:competencias`.

## Completion criteria

The run is done when all of the following hold:

- The diff keeps every **Decided** rule and the **Result** formula
- Questionnaire id `competencias` still grants the student seal once
- Each **Open** line is unchanged, or the human closed it by editing this file
- Trail changes are absent from `feat/questionario-a`

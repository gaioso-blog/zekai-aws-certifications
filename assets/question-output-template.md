# Question Output Templates

This file contains the output templates for all question types and modes.
Use the appropriate template based on the active mode and question type.

---

## Study Mode — Single-choice question

### Questao {{number}} — {{domain}}

**Exame:** {{exam_name}}
**Codigo:** {{exam_code}}
**Nivel:** {{difficulty}}
**Dominio:** {{domain}}
**Topico:** {{topic}}
**Base no guia:** {{exam_guide_reference}}

{{question}}

A. {{option_a}}
B. {{option_b}}
C. {{option_c}}
D. {{option_d}}

**Resposta correta:** {{correct_answer}}

**Por que esta correta:**
{{correct_explanation}}

**Por que as outras estao erradas:**
- **A:** {{option_a_explanation}}
- **B:** {{option_b_explanation}}
- **C:** {{option_c_explanation}}
- **D:** {{option_d_explanation}}

**Por que essa questao e dificil:**
{{why_question_is_difficult}}

**Pegadinha da prova:**
{{exam_trap}}

**Resumo para revisao:**
{{summary}}

**Documentacao AWS recomendada:**
{{recommended_docs}}

---

## Interactive Quiz Mode — Before user answers (single-choice)

### Questao {{number}} — {{domain}}

**Exame:** {{exam_name}}
**Codigo:** {{exam_code}}
**Nivel:** {{difficulty}}
**Dominio:** {{domain}}
**Topico:** {{topic}}
**Base no guia:** {{exam_guide_reference}}

{{question}}

A. {{option_a}}
B. {{option_b}}
C. {{option_c}}
D. {{option_d}}

Responda apenas com **A, B, C ou D**.

DO NOT include: correct answer, explanation, why difficult, trap, summary, docs.

---

## Interactive Quiz Mode — After user answers (single-choice)

## Resultado

**Sua resposta:** {{user_answer}}
**Resposta correta:** {{correct_answer}}
**Status:** {{Correto | Incorreto}}

## Validacao

[If correct]: Correto. Voce acertou porque {{short_reason}}.
[If incorrect]: Incorreto. A alternativa **{{user_answer}}** parece plausivel, mas esta errada porque {{why_user_answer_is_wrong}}.

## Por que a correta e a melhor resposta

{{correct_explanation_full}}

## Por que as outras estao erradas

- **A:** Parece plausivel porque {{why_tempting}}. Porem, falha porque {{specific_failure}}.
- **B:** {{option_b_explanation}}
- **C:** {{option_c_explanation}}
- **D:** {{option_d_explanation}}

## Por que essa questao e dificil

{{why_question_is_difficult}}

## Referencias oficiais AWS

{{aws_docs}}

## Pegadinha da prova

{{exam_trap}}

## Resumo para revisao

{{summary}}

## Proxima acao

Quer que eu gere a proxima questao?

---

## Study Mode — Multiple-response question

### Questao {{number}} — {{domain}}

**Exame:** {{exam_name}}
**Codigo:** {{exam_code}}
**Nivel:** {{difficulty}}
**Tipo:** Multipla resposta
**Quantidade de respostas corretas:** {{number_of_correct_answers}}
**Dominio:** {{domain}}
**Topico:** {{topic}}
**Base no guia:** {{exam_guide_reference}}

{{question}}

A. {{option_a}}
B. {{option_b}}
C. {{option_c}}
D. {{option_d}}
E. {{option_e}}

**Respostas corretas:** {{correct_letters}}

**Por que estao corretas:**
- **{{letter_1}}:** {{explanation}}
- **{{letter_2}}:** {{explanation}}

**Por que as outras estao erradas:**
- **A:** {{option_a_explanation}}
- **B:** {{option_b_explanation}}
- **C:** {{option_c_explanation}}
- **D:** {{option_d_explanation}}
- **E:** {{option_e_explanation}}

**Por que essa questao e dificil:**
{{why_question_is_difficult}}

**Pegadinha da prova:**
{{exam_trap}}

**Resumo para revisao:**
{{summary}}

**Documentacao AWS recomendada:**
{{recommended_docs}}

---

## Interactive Quiz Mode — Before user answers (multiple-response)

### Questao {{number}} — {{domain}}

**Exame:** {{exam_name}}
**Codigo:** {{exam_code}}
**Nivel:** {{difficulty}}
**Tipo:** Multipla resposta
**Quantidade de respostas corretas:** {{number_of_correct_answers}}
**Dominio:** {{domain}}
**Topico:** {{topic}}
**Base no guia:** {{exam_guide_reference}}

{{question}}

A. {{option_a}}
B. {{option_b}}
C. {{option_c}}
D. {{option_d}}
E. {{option_e}}

Responda com **{{number_of_correct_answers}} alternativas**, por exemplo: **A, C**.

DO NOT include: correct answers, explanations, why difficult, trap, summary, docs.

---

## Interactive Quiz Mode — After user answers (multiple-response)

## Resultado

**Sua resposta:** {{user_answers}}
**Respostas corretas:** {{correct_letters}}
**Status:** {{Correto | Parcialmente correto | Incorreto}}

## Validacao

[If wrong letter count]: Você selecionou {{n}} alternativa(s), mas esta questão exige {{required}}. Por favor, reenvie sua resposta com {{required}} alternativas, por exemplo: **A, C**. (Do NOT reveal correct answers.)
[If fully correct]: Correto. Voce selecionou todas as alternativas corretas.
[If partial]: Parcialmente correto. Você acertou {{correct_selected}} mas faltou {{missing_letters}}. Veja a explicação abaixo.
[If incorrect]: Incorreto. Veja a explicação abaixo para entender por que cada alternativa está certa ou errada.

## Por que as corretas sao as melhores respostas

- **{{correct_letter_1}}:** {{explanation}}
- **{{correct_letter_2}}:** {{explanation}}

## Por que as outras estao erradas

- **A:** {{option_a_explanation}}
- **B:** {{option_b_explanation}}
- **C:** {{option_c_explanation}}
- **D:** {{option_d_explanation}}
- **E:** {{option_e_explanation}}

## Por que essa questao e dificil

{{why_question_is_difficult}}

## Referencias oficiais AWS

{{aws_docs}}

## Pegadinha da prova

{{exam_trap}}

## Resumo para revisao

{{summary}}

## Proxima acao

Quer que eu gere a proxima questao?

---

## Session progress summary (show every 5 questions or on request)

**Progresso:** Questao {{n}} | Corretas: {{correct}} | Erradas: {{incorrect}} | Dominio atual: {{domain}}

---

## End-of-session summary

## Resultado Final

**Pontuacao:** {{correct}}/{{total}} ({{percent}}%)

**Dominios com erros:**
{{domains_with_errors}}

**Recomendacao de revisao:**
{{review_recommendation}}

**Documentacao AWS sugerida:**
{{aws_docs_for_weak_areas}}

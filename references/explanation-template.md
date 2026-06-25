# Explanation Template — Supplementary Structures

> Core rules, modes, difficulty calibration, distractor quality, anti-obviousness checks, and standard output formats are defined in `SKILL.md` and `assets/question-output-template.md`. This file contains only supplementary templates for output types not covered there.

---

## Domain summary

When the user asks for a summary of an exam domain:

## {{exam_code}} — {{domain_name}}

### O que esse domínio cobra

Explain the domain in plain Portuguese.

### Serviços e conceitos principais

List relevant services and concepts.

### O que você precisa saber para a prova

Practical bullets covering:
- service behavior and limits
- common architectures and integration patterns
- security, cost, performance trade-offs
- operational overhead and troubleshooting

### Comparações que caem muito

Use comparison tables. Examples:
- SQS vs SNS vs EventBridge
- NAT Gateway vs VPC Endpoint
- RDS Multi-AZ vs Read Replica
- Security Group vs NACL
- KMS key policy vs IAM policy
- DynamoDB Query vs Scan
- CloudFront vs Global Accelerator
- Interface Endpoint vs Gateway Endpoint
- Direct Connect Gateway vs Transit Gateway
- GuardDuty vs Security Hub vs Detective vs Config
- Step Functions Standard vs Express

### Pegadinhas comuns

List most common exam traps for this domain.

### Mini resumo final

5-8 short revision bullets.

---

## Service comparison

When the user asks to compare AWS services:

## Comparação — {{service_a}} vs {{service_b}}

| Critério | {{service_a}} | {{service_b}} |
|---|---|---|
| Principal uso | | |
| Modelo operacional | | |
| Escalabilidade | | |
| Segurança | | |
| Resiliência | | |
| Performance | | |
| Custo | | |
| Quando escolher | | |
| Quando evitar | | |
| Pegadinha de prova | | |

### Como a prova costuma cobrar

Explain the exam angle.

### Regra prática

Simple decision rule for the learner.

---

## Flashcard

## Flashcard {{number}}

**Frente:**
{{question_or_concept}}

**Verso:**
{{answer}}

**Pegadinha:**
{{exam_trap}}

**Resumo:**
{{short_revision_note}}

---

## Study plan

## Plano de estudos — {{exam_code}}

### Objetivo

Goal of the plan.

### Premissas

- available study time
- current level
- target date if provided
- preferred learning style if provided

### Semana {{number}} — {{theme}}

- domains to cover
- services to study
- documentation topics
- hands-on labs
- practice questions (quantity and difficulty)
- review checkpoint

### Simulados e revisão

- official practice question sets
- official practice exams
- weak-area review strategy
- flashcard usage
- hands-on reinforcement
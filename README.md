# Zekai AWS Certifications

> Skill para Kiro CLI que gera questões originais de certificação AWS com raciocínio inteligente, dificuldade adaptativa e explicações detalhadas — baseada nos Guias Oficiais de Exame da AWS.

[![Kiro CLI](https://img.shields.io/badge/plataforma-Kiro%20CLI-purple)]()

---

## Visão Geral

Esta skill transforma seu agente Kiro CLI em um coach especializado para certificações AWS. Ela gera questões originais baseadas em cenários que exigem raciocínio através de trade-offs e constraints, não memorização de keywords.

Diferente de geradores genéricos de questões, esta skill implementa um sistema de qualidade em múltiplas camadas:
- **Verificações anti-obviedade** garantem que questões difíceis não possam ser resolvidas por eliminação simples
- **Distratores near-miss** testam diferenças sutis entre serviços AWS similares
- **Dificuldade adaptativa** responde ao seu desempenho em tempo real
- **Persistência de estado** mantém o tracking de sessão em simulados longos

Cada questão é mapeada a um domínio e task statement do Guia Oficial de Exame da AWS.

---

## Certificações Suportadas

| Código | Certificação | Nível |
|--------|-------------|-------|
| CLF-C02 | AWS Certified Cloud Practitioner | Foundational |
| SAA-C03 | AWS Certified Solutions Architect – Associate | Associate |
| DVA-C02 | AWS Certified Developer – Associate | Associate |
| SOA-C02 | AWS Certified SysOps Administrator – Associate | Associate |
| DEA-C01 | AWS Certified Data Engineer – Associate | Associate |
| MLA-C01 | AWS Certified Machine Learning Engineer – Associate | Associate |
| AIF-C01 | AWS Certified AI Practitioner | Foundational |
| SAP-C02 | AWS Certified Solutions Architect – Professional | Professional |
| DOP-C02 | AWS Certified DevOps Engineer – Professional | Professional |
| AIP-C01 | AWS Certified Generative AI Developer – Professional | Professional |
| ANS-C01 | AWS Certified Advanced Networking – Specialty | Specialty |
| SCS-C02 | AWS Certified Security – Specialty | Specialty |

---

## Como Funciona

### Fluxo de Raciocínio do Agente

Quando o usuário solicita uma questão, o agente segue este pipeline interno:

```
┌─────────────────────────────────────────────────────────────────┐
│  1. IDENTIFICAR                                                  │
│     Reconhecer exame → Resolver domínio → Selecionar task        │
│     statement do guia oficial                                    │
├─────────────────────────────────────────────────────────────────┤
│  2. CONSTRUIR CENÁRIO                                            │
│     Montar cenário realista → Adicionar constraints (negócio +   │
│     técnico + segurança + operacional + custo/resiliência)       │
├─────────────────────────────────────────────────────────────────┤
│  3. ENGENHARIA DE DISTRATORES                                    │
│     Criar opções near-miss → Cada uma falha por UM requisito     │
│     específico → Todas similares em tamanho e qualidade          │
├─────────────────────────────────────────────────────────────────┤
│  4. GATE ANTI-OBVIEDADE (silencioso)                             │
│     Resposta adivinhável por keywords? → Reescrever              │
│     Iniciante elimina 2 opções de cara? → Fortalecer             │
│     Opção correta é a única detalhada? → Equalizar todas         │
├─────────────────────────────────────────────────────────────────┤
│  5. OUTPUT                                                       │
│     Modo Estudo → Explicação completa imediatamente              │
│     Modo Interativo → Apenas questão, aguardar resposta          │
└─────────────────────────────────────────────────────────────────┘
```

### Engenharia de Distratores

Cada alternativa errada é projetada para ser **plausível em algum contexto AWS** mas incorreta para o cenário específico. A skill utiliza 18 famílias de comparação para construir distratores fortes:

| Família de Comparação | O que Testa |
|---|---|
| SQS Standard vs FIFO vs EventBridge vs Kinesis | Trade-offs de processamento de eventos |
| RDS Multi-AZ vs Read Replica vs Aurora Global | HA vs escalabilidade de leitura vs DR |
| Gateway Endpoint vs Interface Endpoint vs NAT GW | Custo e escopo de acesso privado |
| CloudFront vs Global Accelerator vs Route 53 | Edge delivery vs aceleração TCP vs roteamento |
| KMS key policy vs IAM policy vs bucket policy vs SCP | Camadas de controle de acesso |
| Step Functions Standard vs Express vs SQS+Lambda | Overhead de orquestração |
| Savings Plans vs RIs vs Spot vs On-Demand | Otimização de pricing |
| Direct Connect GW vs Transit GW vs VPN vs Cloud WAN | Conectividade híbrida |

Cada questão difícil inclui pelo menos um **distrator near-miss**, uma opção que seria correta se um requisito do cenário fosse removido.

---

## Modos de Interação

### Modo Quiz Interativo (Recomendado)

Simula a experiência real de prova. Uma questão por vez, você responde primeiro, depois recebe a validação completa.

```
Usuário: Simulado SAA-C03 hard

Agente:  ### Questão 1 — Design Resilient Architectures
         [cenário com constraints]
         A. [opção]  B. [opção]  C. [opção]  D. [opção]
         Responda apenas com A, B, C ou D.

Usuário: B

Agente:  ## Resultado
         Sua resposta: B | Resposta correta: C | Status: Incorreto
         
         ## Validação
         Incorreto. A alternativa B parece plausível porque...
         
         ## Por que a correta é a melhor resposta
         [raciocínio detalhado]
         
         ## Por que as outras estão erradas
         [cada opção explicada]
         
         ## Pegadinha da prova
         [explicação do trap oculto]
         
         [STATE: Q=1 C=0 E=1 DOM=Design Resilient Architectures]
```

**Funcionalidades da sessão:**
- Resumo de progresso a cada 10 questões
- Dificuldade adaptativa (aumenta após 3 acertos consecutivos)
- Explicação de conceito oferecida após 2 erros no mesmo domínio
- Encerramento semântico — reconhece "pode parar", "chega", "obrigado", "até mais" além dos comandos explícitos
- Relatório final com pontuação, domínios fracos e recomendações de estudo
- Persistência de estado via marcadores `[STATE: ...]` — sobrevive a sessões longas com compactação de contexto

### Modo Estudo

Explicação completa entregue imediatamente. Ideal para revisão e reforço de conceitos.

```
Usuário: Gera 3 questões de SAA-C03 com explicação, nível hard
```

Cada questão inclui: cenário, alternativas, resposta correta, explicação de cada opção, pegadinha, resumo para revisão e referências de documentação AWS.

> Padrão: 10 questões quando o número não é especificado.

---

## Níveis de Dificuldade

| Nível | Constraints | Qualidade dos Distratores | Público-alvo |
|-------|------------|--------------------------|--------------|
| **Easy** | 1 requisito | Diretos | Iniciantes |
| **Medium** | 2-3 requisitos | 1 distrator plausível | Estudo ativo |
| **Hard** | 3-5 requisitos | 2+ plausíveis, 1 near-miss | Pré-prova |
| **Exam-level** | 4+ requisitos + trade-offs | Todas plausíveis | Preparação final |

Para questões hard e exam-level, a skill verifica:
- Resposta não pode ser adivinhada por keyword matching
- Pelo menos 2 distratores exigem conhecimento real de AWS para eliminar
- Cada resposta errada falha por um motivo específico e explicável
- Todas as opções são similares em tamanho, detalhe e tom profissional

---

## Tipos de Output Suportados

| Tipo | Descrição |
|------|-----------|
| Questões múltipla escolha | Formato padrão com 4 opções |
| Questões múltipla resposta | 2-3 corretas de 5 opções |
| Questões baseadas em cenário | Decisões arquiteturais reais |
| Quizzes interativos | Uma por vez com validação |
| Sessões de simulado | Sessões completas com pontuação |
| Validação de respostas | Explicar por que uma resposta está certa/errada |
| Explicação de questões existentes | Analisar questões de outras fontes |
| Resumos / flashcards | Revisão concisa por domínio |
| Planos de estudo | Preparação semanal estruturada |
| Tabelas comparativas de serviços | Side-by-side com ângulo de prova |
| Pegadinhas e armadilhas | Pontos comuns de confusão |
| Folhas de revisão | Bullets por domínio |

---

## Quick Start

### Pré-requisitos

- [Kiro CLI](https://kiro.dev/docs/) instalado e configurado
- **AWS MCP Server** configurado no Kiro (recomendado) — permite buscar os guias oficiais de exame em tempo real via `aws___search_documentation` e `aws___read_documentation`. Sem ele, a skill opera com conhecimento interno e informa o usuário.

### Instalação

Copie o diretório da skill para sua pasta de skills do Kiro:

```bash
cp -r zekai-aws-certifications ~/.kiro/skills/
```

Ou clone o repositório:

```bash
git clone <repository-url> ~/.kiro/skills/zekai-aws-certifications
```

### Registrar no agente

Para que o Kiro carregue a skill sob demanda, adicione a referência `skill://` na configuração do agente (`~/.kiro/agents/<nome>.json`):

```json
{
  "resources": [
    "skill://~/.kiro/skills/zekai-aws-certifications/SKILL.md"
  ]
}
```

Se usar o agente padrão (`kiro_default`), a skill é carregada automaticamente por estar na pasta `~/.kiro/skills/` — nenhuma configuração adicional é necessária.

### Verificar carregamento

Use `/context show` no Kiro CLI para confirmar que a skill aparece na lista de recursos carregados.

### Exemplos de Uso

```
# Simulado interativo
Simulado interativo SAA-C03 exam-level

# Modo estudo com explicações
Gera 5 questões de DVA-C02 com explicação completa

# Prática por domínio
Quiz de segurança para SCS-C02, nível hard

# Explicar questão existente
[cole a questão] — Qual a resposta correta e por quê?

# Comparação de serviços
Compara Gateway Endpoint vs Interface Endpoint vs NAT Gateway

# Plano de estudos
Monta plano de estudos de 4 semanas para SAP-C02

# Flashcards
Flashcards de DynamoDB para DEA-C01

# Modo debug — auditar qualidade das questões
modo debug — simulado SAA-C03 exam-level

# Código em minúsculas funciona normalmente
simulado saa-c03 hard
```

> Códigos de exame são normalizados automaticamente para uppercase. Códigos não suportados retornam mensagem de erro com a lista dos disponíveis.

---

## Arquitetura

```
zekai-aws-certifications/
├── SKILL.md                              # Comportamento, regras e formatos de output
├── README.md                             # Este arquivo (PT-BR)
├── README.en.md                          # English version
├── references/
│   ├── exam-guides.md                    # Códigos, nomes e notas sobre exames suportados
│   ├── aws-service-by-exam.md            # Mapeamento serviço → domínio por exame
│   └── explanation-template.md           # Templates suplementares (resumos, comparações, flashcards)
└── assets/
    └── question-output-template.md       # Templates estruturados de output por modo
```

### Princípios de Design

| Princípio | Implementação |
|-----------|---------------|
| **Fonte de verdade** | Guia Oficial AWS via AWS MCP Server (`aws___search_documentation` + `aws___read_documentation`) |
| **Anti-alucinação** | Nunca inventa domínios, task statements ou escopo |
| **Anti-pirataria** | Gera apenas conteúdo original — sem questões copiadas |
| **Eficiência de contexto** | Regras consolidadas, sem redundância |
| **Resiliência de estado** | Marcadores `[STATE:]` com 7 campos sobrevivem a compactação de contexto |
| **Adaptativo** | Dificuldade responde ao desempenho do learner |
| **Idioma dinâmico** | Responde no idioma em que o usuário escreve |

---

## Regras Core

A skill impõe 7 regras invariáveis em todos os modos:

1. **Idioma** — Responde no idioma em que o usuário escreve. Override apenas se o usuário solicitar explicitamente outro idioma.
2. **Fonte de verdade** — Guia Oficial AWS (via AWS MCP Server) > memória > referências locais
3. **Anti-pirataria** — Sem reprodução de questões proprietárias de qualquer provider
4. **Anti-alucinação** — Sem domínios, task statements ou percentuais fabricados
5. **Sigilo de resposta** — Nunca revela resposta, dica, opinião sobre opções ou qualquer informação indireta que possa levar à resposta antes do usuário responder (Modo Interativo)
6. **Uma melhor resposta** — Toda questão tem exatamente uma melhor resposta inequívoca
7. **Baseada em cenário** — Prioriza raciocínio sobre trivia

---

## Como as Questões São Validadas

Antes de outputar qualquer questão hard ou exam-level, o agente executa um gate de qualidade com 7 itens:

| Verificação | Ação se Falhar |
|-------------|---------------|
| Resposta adivinhável por keyword matching? | Reescrever questão |
| Menos de 2 distratores plausíveis? | Melhorar opções |
| Opção errada não falha por requisito específico? | Reescrever opção |
| Opção correta é a única em linguagem de best-practice? | Equalizar todas |
| Cenário sem constraints suficientes? | Adicionar constraints |
| Iniciante elimina 2 opções imediatamente? | Fortalecer distratores |
| Resposta correta se revela por ser a única mencionando o serviço-chave? | Adicionar alternativas |

Por padrão esse gate é **silencioso**, o usuário não vê sua execução.

### Modo Debug

Para auditar o gate de qualidade em tempo real, ative o modo debug:

```
modo debug — simulado SAA-C03 exam-level
```

Com o debug ativo, cada questão hard/exam-level é precedida por um bloco de auditoria:

```
[QUALITY CHECK]
1. keyword-proof ✓
2. 2+ plausible distractors ✓
3. each wrong fails specific requirement ✓
4. correct not only best-practice option ✓
5. enough constraints ✓
6. beginner can't eliminate 2 immediately ✓
7. key service not exclusive to correct option ✓
rewrites: 1 — strengthened distractor C to include RDS Multi-AZ context
```

Para desativar: `debug off` ou `modo normal`.

---

## Tracking de Sessão

Durante sessões interativas, a skill mantém:

- Contagem de questões
- Acertos e erros
- Domínios cobertos e domínios com erros
- Sequências de acertos/erros consecutivos (para dificuldade adaptativa)

O estado é persistido via marcadores visíveis:

```
[STATE: Q=7 C=5 E=2 EXAM=SAA-C03 DIFF=hard DBG=off DOM=Design Resilient Architectures, Security]
```

O marcador persiste: número da questão, acertos, erros, exame, dificuldade, estado do debug mode e domínios com erros. Isso garante recuperação completa mesmo após compactação de contexto em sessões longas.

`DOM=` usa vírgula como separador. `DOM=∅` quando não há erros.

### Relatório de Fim de Sessão

```
Resultado final: 8/10 (80%)
Domínios com erros: Design Resilient Architectures, Security
Recomendação: Revisar Multi-AZ vs Read Replica, KMS key policies
Documentação sugerida: [links]
```

## Referências

- [AWS Certification Exam Guides](https://docs.aws.amazon.com/aws-certification/latest/examguides/aws-certification-exam-guides.html) — Fonte primária de verdade
- [Kiro CLI](https://kiro.dev/docs/cli/) — Documentação do Kiro
- [AWS Well-Architected Framework](https://docs.aws.amazon.com/wellarchitected/latest/framework/welcome.html) — Princípios de design referenciados nas questões

---

> **Aviso Legal:** Esta skill gera questões originais de prática para fins educacionais. Ela não contém, reproduz ou deriva de questões reais de exames de certificação AWS, exam dumps ou conteúdo proprietário de qualquer provedor de preparação para exames. Todo o conteúdo é inspirado em documentação AWS publicamente disponível e guias oficiais de exame.
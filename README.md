# NailTime

NailTime é uma plataforma de agendamento para manicure e nail designer, construída com React, Node.js, TypeScript e PostgreSQL.

O sistema possui uma área pública para apresentação dos serviços, galeria e agendamento de horários, além de uma área administrativa para gerenciamento da agenda, serviços, disponibilidade, bloqueios, imagens e personalização da identidade visual do negócio.

## Fonte de verdade do projeto

Este repositório é o ponto central de comunicação entre todas as etapas de desenvolvimento.

As conversas utilizadas durante o desenvolvimento não dependem de memória compartilhada. Cada etapa deve utilizar os documentos versionados neste repositório como fonte de verdade.

O fluxo obrigatório do projeto é:

Constituição  
→ Spec  
→ Clarificação  
→ Planejamento  
→ Implementação com TDD  
→ Análise / Validação

Os principais artefatos são mantidos em:

```text
docs/
├── constitution.md
├── spec.md
├── clarification.md
├── decisions.md
├── plan.md
├── implementation-report.md
├── audit.md
└── adr/
```

Cada etapa deve ler apenas os documentos necessários, produzir seu artefato correspondente e salvá-lo no repositório para utilização pela próxima etapa.

## Princípio de rastreabilidade

Decisões e implementações devem manter relação explícita entre:

```text
REQ → TASK → TEST → AUDIT
```

Exemplo:

```text
REQ-APT-014
    ↓
TASK-APT-021
    ↓
TEST-APT-032
    ↓
AUDIT-APT-014
```

O histórico das conversas não é considerado documentação oficial do projeto. Decisões relevantes devem ser registradas nos arquivos do repositório.

# DocForge

**Forje sua documentação antes de forjar seu código.**

![Version](https://img.shields.io/badge/version-0.1.0-blue)
![License](https://img.shields.io/badge/license-MIT-green)
![Language](https://img.shields.io/badge/lang-pt--BR-yellow)
![Claude Code](https://img.shields.io/badge/Claude%20Code-compatible-orange)

Um framework documentation-first que guia desenvolvedores na criação de documentação de software adequada antes de escrever código, através de fluxos de trabalho interativos assistidos por IA.

## O que é isso?

Este repositório fornece um fluxo estruturado para criar documentação de software **antes** de codar. Você interage com um agente de IA (Claude Code) executando comandos em sequência, e ao final terá todos os documentos essenciais para iniciar o desenvolvimento.

## Por quê?

Documentação de design não é burocracia. É a diferença entre construir algo que funciona e construir algo que resolve o problema certo.

**Para desenvolvimento tradicional:**
- Reduz retrabalho ao alinhar expectativas antes de escrever código
- Facilita onboarding de novos membros da equipe
- Cria registro histórico de decisões técnicas (ADRs)
- Força você a pensar nos edge cases antes de encontrá-los em produção

**Para desenvolvimento com agentes de IA:**
- Agentes de IA são excelentes executores, mas precisam de contexto claro
- Sem documentação, o agente "adivinha" requisitos e arquitetura
- Com documentação, o agente tem um contrato explícito do que construir
- PRDs e FDDs funcionam como prompts estruturados de alta qualidade
- User Stories com critérios BDD se tornam testes verificáveis
- O agente pode referenciar ADRs para manter consistência arquitetural

**O paradoxo da velocidade:**
Parece mais rápido pular direto para o código. Mas sem documentação clara, você gasta mais tempo corrigindo mal-entendidos, refatorando decisões ruins e explicando o sistema repetidamente. Com agentes de IA, esse problema se amplifica: o agente trabalha rápido, mas na direção errada.

Investir 30 minutos em documentação pode economizar horas de retrabalho.

## Quick Start

1. Clone este repositório
2. Abra no terminal com Claude Code
3. Execute `/prd-create` para começar

## Fluxo de Documentação

### Novo Projeto (Fluxo Completo)

```
/prd-create ──► /user-stories-create ──► /hld-create
     │                   │                    │
     ▼                   ▼                    ▼
docs/project/       docs/project/        docs/project/
PRD.md              USER-STORIES.md      HLD.md
                                              │
                                              ▼
                              /c4-diagram-create + /mermaid-diagram-create
                                              │
                                              ▼
                              /deep-research-1 + /deep-research-2 (opcional)
                                              │
                                              ▼
                                        /adr-create (×N)
                                              │
                                              ▼
                                    docs/project/adrs/
```

### Nova Feature (Fluxo de Feature)

```
/prd-create ──► /user-stories-create ──► /deep-research-1 + /deep-research-2 (opcional*)
(feature)              │                              │
     │                 ▼                              ▼
docs/features/   docs/features/                 docs/features/
[nome]/PRD.md    [nome]/USER-STORIES.md         [nome]/research/
                                                      │
                                                      ▼
                                                /fdd-create
                                                      │
                                                      ▼
                                            docs/features/[nome]/FDD.md
                                                      │
                                                      ▼
                              /c4-diagram-create + /mermaid-diagram-create
                                                      │
                                                      ▼
                                        docs/features/[nome]/diagrams/

* opcional, mas se iniciar fase 1, completar fase 2
```

## Comandos Disponíveis

| Comando | Propósito | Output |
|---------|-----------|--------|
| `/prd-create` | Criar Product Requirements Document | PRD.md |
| `/user-stories-create` | Criar User Stories com critérios de aceite BDD | USER-STORIES.md |
| `/hld-create` | Criar High Level Design | HLD.md |
| `/fdd-create` | Criar Feature Design Document | FDD.md |
| `/adr-create` | Criar Architecture Decision Record | ADR-XXXX.md |
| `/deep-research-1` | Fase 1 do deep research | Contexto de pesquisa |
| `/deep-research-2` | Fase 2 do deep research | RESEARCH-[topico].md |
| `/c4-diagram-create` | Criar diagramas C4 de arquitetura | arquivos .puml |
| `/mermaid-diagram-create` | Criar diagramas Mermaid | diagrams.md |

## Tipos de Documento

| Documento | Nível | Propósito |
|-----------|-------|-----------|
| **PRD** | Projeto ou Feature | POR QUÊ e O QUÊ - requisitos de negócio, escopo, métricas |
| **User Stories** | Projeto ou Feature | QUEM quer O QUÊ - comportamentos do usuário com critérios de aceite |
| **HLD** | Projeto | COMO (alto nível) - arquitetura do sistema, componentes |
| **FDD** | Feature | COMO (detalhado) - detalhes técnicos de implementação |
| **ADR** | Projeto ou Feature | POR QUÊ essa decisão - decisões arquiteturais com trade-offs |

## Estrutura de Pastas

```
docs/
├── PROGRESS.md          # Acompanha seu progresso no fluxo de documentação
├── ADRs.md              # Índice de todas as ADRs com metadados
├── docs-notes.md        # Material de referência sobre tipos de documentação
│
├── project/             # Documentos de nível de projeto
│   ├── PRD.md
│   ├── USER-STORIES.md
│   ├── HLD.md
│   ├── research/        # Outputs de deep research
│   ├── adrs/            # ADRs de nível de projeto
│   ├── c4/              # Diagramas C4 do projeto
│   └── diagrams/        # Diagramas Mermaid do projeto
│
└── features/            # Documentos de nível de feature
    └── [nome-da-feature]/
        ├── PRD.md
        ├── USER-STORIES.md
        ├── FDD.md
        ├── research/    # Research da feature (se necessário)
        ├── adrs/        # ADRs específicas da feature
        ├── c4/          # Diagramas C4
        └── diagrams/    # Diagramas Mermaid
```

## Dicas de Workflow

1. **Após cada comando**, a IA mostrará seu progresso e indicará o próximo passo
2. **Execute `/clear`** entre comandos para limpar o contexto e começar fresco
3. **Verifique `docs/PROGRESS.md`** para ver onde você está no fluxo
4. **ADRs são numeradas globalmente** - verifique `docs/ADRs.md` para o número atual

## Criando um Novo Projeto vs Nova Feature

### Novo Projeto
Comece com `/prd-create` e siga o fluxo completo. Isso cria documentação de nível de sistema em `docs/project/`.

### Nova Feature
Comece com `/prd-create` para a feature. Quando perguntado, especifique que é para um sistema existente. Documentos vão para `docs/features/[nome-da-feature]/`.

## Referências

- [C4 Model](https://c4model.com/)
- [MADR - Markdown ADRs](https://adr.github.io/madr/)
- [Mermaid Docs](https://mermaid.js.org/)

## Créditos

Grande parte dos prompts em `.claude/` foram desenvolvidos por **Wesley Williams** durante o MBA em Engenharia de Software com IA na **Full Cycle**. Este repositório adapta, expande e organiza esse material em um framework reutilizável.


## Apoie

Se este framework te ajudou a escrever documentação melhor, considere dar uma ⭐ — isso ajuda outras pessoas a descobrirem o projeto!

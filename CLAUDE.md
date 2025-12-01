# CLAUDE.md

Este arquivo fornece orientações ao Claude Code ao trabalhar com este repositório.

## Visão Geral do Projeto

Este é um Framework de Documentação de Software - um repositório boilerplate que ajuda desenvolvedores a criar documentação adequada antes de começar a codar. Usuários interagem com o Claude Code executando slash commands em sequência.

## Arquivos e Pastas Principais

- `docs/PROGRESS.md` - Acompanha o progresso do usuário no fluxo de documentação. Atualize após cada documento criado.
- `docs/ADRs.md` - Índice global de todas as ADRs. Verifique aqui para o próximo número de ADR.
- `docs/project/` - Documentação de nível de projeto (PRD, HLD, User Stories, ADRs, research)
- `docs/features/` - Documentação de nível de feature, organizada por nome de feature
- `.claude/commands/` - Definições de slash commands para criação de documentos
- `.claude/agents/` - Definições de agentes para geração de diagramas

## Comandos Disponíveis

| Comando | Cria |
|---------|------|
| `/prd-create` | PRD (Product Requirements Document) |
| `/user-stories-create` | User Stories com critérios de aceite BDD |
| `/hld-create` | HLD (High Level Design) |
| `/fdd-create` | FDD (Feature Design Document) |
| `/adr-create` | ADR (Architecture Decision Record) |
| `/deep-research-1` | Deep research fase 1 |
| `/deep-research-2` | Deep research fase 2 |
| `/c4-diagram-create` | Diagramas de arquitetura C4 |
| `/mermaid-diagram-create` | Diagramas Mermaid |

## Fluxo de Documentos

### Novo Projeto
1. `/prd-create` → `docs/project/PRD.md`
2. `/user-stories-create` → `docs/project/USER-STORIES.md`
3. `/hld-create` → `docs/project/HLD.md`
4. `/c4-diagram-create` + `/mermaid-diagram-create` → `docs/project/c4/` e `docs/project/diagrams/`
5. `/deep-research-1` + `/deep-research-2` → `docs/project/research/` *(opcional, mas se iniciar fase 1, completar fase 2)*
6. `/adr-create` (repetir conforme necessário) → `docs/project/adrs/`

### Nova Feature
1. `/prd-create` → `docs/features/[nome]/PRD.md`
2. `/user-stories-create` → `docs/features/[nome]/USER-STORIES.md`
3. `/deep-research-1` + `/deep-research-2` → `docs/features/[nome]/research/` *(opcional, mas se iniciar fase 1, completar fase 2)*
4. `/fdd-create` → `docs/features/[nome]/FDD.md`
5. `/c4-diagram-create` + `/mermaid-diagram-create` → `docs/features/[nome]/diagrams/`
6. `/adr-create` (se necessário) → `docs/features/[nome]/adrs/`

## Após Criar um Documento

Após criar um documento com sucesso:

1. **Atualize `docs/PROGRESS.md`**:
   - Marque o passo completado com `[x]`
   - Adicione `◄── VOCÊ ESTÁ AQUI` no próximo passo
   - Atualize o timestamp de `Last Updated`
   - Atualize o número de `Current Step`

2. **Mostre o resumo de progresso** para o usuário:
   ```
   ---
   Progresso: [X/Y] documentos completados

   Completados:
   - [x] PRD
   - [x] User Stories

   Próximo passo: Execute `/clear` para limpar o contexto, depois execute `/hld-create`
   ---
   ```

3. **Se criando uma ADR**, também atualize `docs/ADRs.md`:
   - Adicione entrada na tabela com todos os metadados
   - Números de ADR são globais/sequenciais em todo o projeto

## Numeração de ADRs

ADRs usam numeração sequencial global independente de onde estão:
- `docs/project/adrs/ADR-0001-*.md`
- `docs/features/login/adrs/ADR-0002-*.md`
- `docs/features/payments/adrs/ADR-0003-*.md`

Antes de criar uma nova ADR, verifique `docs/ADRs.md` para determinar o próximo número.

## Regras de Localização de Arquivos

| Tipo de Documento | Nível de Projeto | Nível de Feature |
|-------------------|------------------|------------------|
| PRD | `docs/project/PRD.md` | `docs/features/[nome]/PRD.md` |
| User Stories | `docs/project/USER-STORIES.md` | `docs/features/[nome]/USER-STORIES.md` |
| HLD | `docs/project/HLD.md` | N/A (HLD é sempre nível de projeto) |
| FDD | N/A (FDD é sempre nível de feature) | `docs/features/[nome]/FDD.md` |
| ADRs | `docs/project/adrs/ADR-XXXX-*.md` | `docs/features/[nome]/adrs/ADR-XXXX-*.md` |
| Research | `docs/project/research/` | `docs/features/[nome]/research/` |
| Diagramas C4 | `docs/project/c4/` | `docs/features/[nome]/c4/` |
| Diagramas Mermaid | `docs/project/diagrams/` | `docs/features/[nome]/diagrams/` |

## Criando Pastas de Feature

Ao criar documentação para uma nova feature:

1. Pergunte ao usuário o nome da feature
2. Crie a estrutura de pastas:
   ```
   docs/features/[nome-da-feature]/
   ├── adrs/
   ├── research/
   ├── c4/
   └── diagrams/
   ```
3. Coloque os documentos nos locais apropriados

## Idioma

- Todos os comandos e templates estão em Português (Brasil)
- Export JSON usa chaves em inglês com valores em português
- README e CLAUDE.md estão em português (exceto termos técnicos)

## Diretrizes de Estilo

- Use português simples e direto
- Uma pergunta por vez durante entrevistas
- Resuma e confirme antes de prosseguir
- Não use travessões do tipo "—"
- Marque suposições como "hipótese"

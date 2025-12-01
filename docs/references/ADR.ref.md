# ADR (Architecture Decision Record)

Um Architecture Decision Record é um documento curto e objetivo que registra uma decisão arquitetural significativa tomada em um projeto. 
Ele normalmente possui a seguinte estrutura:

- Contexto: o problema, motivação e restrições
- Decisão: a solução adotada
- Alternativas: o que foi considerado e descartado
- Consequências: efeitos e implicações da decisão

Função em um "ecosistema de documentação"

Complemento "vivo" documentos como PRD / HLD / FDD, entre outros

- PRD/HLD dizem o que e como a solução será estruturada
- ADR explique o por que uma decisão técnica foi tomada
- LLD mostra como ela se materializa no código

**Regra geral:** Se algo foi debatido, teve trade-offs e impacto no design do sistema, devemos gerar um ADR.

## Estrutura "clássica" Michel Nygard (2011)

ADR-001: Usar Redis como cache distribuído

Contexto:

- Descreve o problema, as restrições e as forças em jogo.

Decisão:

- Explica a solução escolhida e o motivo.

Alternativas Consideradas:

- Lista as opções avaliadas e por que foram rejeitadas.

Consequências:

- O que muda, benefícios e riscos da decisão.

Referências:

- Links para PRD, HLD, RFCs e FDDs.


## MADR (Markdown ADR)

O MADR (Markdown Architecture Decision Record) é um formato padronizado em Markdown para registrar decisões arquiteturais de forma legível e processável.

Ele evoluiu do modelo original de ADR de Michael Nygard, trazendo consistência, metadados e previsibilidade.

Principais pontos:
- Campos padronizados: Status, Date, Tags, Supersedes
- Estrutura fixa e validável em pipelines (se necessário)
- Compatibilidade com ferramentas (adr-tools e adr-log)
- Facilita rastreamento, visualização e documentação contínua

### Exemplo MADR

ADR-003: Escolher gRPC para comunicação interna
Status: Supersedes ADR-002
Date: 2027-03-10
Relates to: ADR-001, ADR-003
Amends: ADR-004
Superseded by: (se for substituído no futuro)
---

Context and Problem Statement:
Descreve o problema, as restrições e o motivo da decisão.

Decision Drivers:
Fatores que influenciaram a escolha (performance, custo, segurança, etc).

Considered Options:
Lista de alternativas analisadas.

Decision Outcome:
Decisão tomada e justificativa principal.

Pros and Cons of the Options:
Resumo dos prós e contras de cada opção.

Consequences:
Impactos técnicos, operacionais e riscos.

References:
Links para PRDs, HLDs, FDDs, RFCs, e ADRs relacionados.

---

## Status de uma ADR
- Proposed: A decisão foi criada, mas ainda está em discussão ou aguardando aprovação.
- Accepted: A decisão foi aprovada e está vigente.
- Rejected: A proposta foi analisada e descartada.
- Deprecated: A decisão continua registrada, mas não deve mais ser usada em novos contextos.
- Superseded: Foi substituída por outro ADR (usado junto com Superseded by: apontando o novo).
- Draft (opcional): Documento em elaboração, ainda sem proposta formal.
- Withdrawn (opcional): A decisão foi retirada antes de ser discutida ou aprovada.

## Metadados importantes para manter ADRs ao longo do tempo:
- Supersedes: Esse ADR substitui outro anterior
- Superseded by: Foi substituído por um ADR mais novo
- Amends: Modifica parcialmente uma decisão antiga
- Relates to: Está tecnicamente relacionado (mas não depende)
- Depends on: Depende de uma decisão anterior para funcionar

Fluxo mais comum:
Draft Proposed -> Accepted -> (Deprecated I Superseeded)

## Boas práticas
- Crie um ADR por decisão, não por sistema inteiro.
- Evite narrativa; seja objetivo e técnico.
- Mantenha nomenclatura consistente (ADR-001, ADR-002...).
- Use pull requests para revisar e aprovar ADRs.
- Sempre inclua links bidirecionais entre ADR e HLD/FDD.
- Marque ADRs desatualizados com Superseeded

## Quando um ADR é necessário (altamente recomendado)

- Decisões que têm impacto arquitetural que acompanharão o projeto por muito tempo
- Afetam vários módulos/componentes/times e que dificilmente mudam com frequência

**Regra geral:** Se a decisão tem implicações em performance, segurança, custo, interoperabilidade ou manutenção, gere um ADR.

### Situação

1. Escolha de tecnologias base (banco de dados, linguagem, framework principal, mensageria)
2. Padrões de comunicação (REST, gRPC, eventos, GraphQL)
3. Estratégia de persistência (SQL, NOSQL, Redis, etc.)
4. Autenticação e autorização (JWT, OAuth2, OpenID Connect)
5. Observabilidade e telemetria (Open Telemetry, Prometheus, tracing)
6. Estratégia de deploy e infraestrutura (Kubernetes, ECS, Cloud Run, Terraform)
7. Padrões de resiliência e fallback (retry, circuit breaker, timeout)
8. Estratégia de Versionamento de APIs
9. Adoação de frameworks ou middlewares proprietários
10. Introdução ou substituição de componentes críticos

### Por que merece um ADR

1. Afeta todo o ciclo de vida do sistema, performance e custos.
2. Define como os serviços interagem e como o sistema se expande.
3. Envolve trade-offs de consistência, disponibilidade e complexidade.
4. Impacta segurança e compatibilidade entre componentes.
5. Crucial para monitoramento e debugging entre times.
6. Define como o sistema escala, é versionado e mantido.
7. Determinam confiabilidade sob falhas e carga alta.
8. Evita quebras contratuais e mantém backward compatibility
9. Introduz dependência organizacional ou de time
10. Ex: trocar RabbitMQ por Kafka, adotar um novo SDK.


## Quando um ADR é opcional (depende)

### Situação

1. Padrão arquitetural local (MVC, Clean Architecure, Hexagonal, etc)
2. Modelagem de domínio (DDD)
3. Organização de pastas e módulos
4. Decisções de design menores (uso de interface, padrão Strategy, Adapter, etc.)
5. Configurações específicas (timeout, batch size, etc.)


### Observação

1. Se a escolha for padrão de time e já adotada em todos os projetos, não precisa de ADR; se for uma mudança de paradigma, sim.
2. Normalmente, não precisa ADR por entidade ou agregado, mas pode haver um ADR para o estilo de modelagem adotado (ex: "usar Aggregate Roots explícitios e Value Objects imutáveis").
3. Documentar em guias de contribuição (CONTRIBUTING.md) ou no
4. Registrar apenas se influenciar a arquitetura ou contratos públicos.
5.  Colocar em comentários no código ou em FDD/LLD


### Exemplo

- Criar um ADR para utilizar DDD em conjunto com Clean Architecture faz sentido se o time migrará de um MVC tradicional para essa nova abordagem.
- Criar um ADR para usar repositórios ao vez de DAO em um microsserviçó pequeno, pode não fazer sentido.

## Quando pode NÃO fazer tanto sentido para a criação de um ADR

Quando a ADR é apenas um "ruído". ADR não é log de decisão operacional.

### Situação

1. Refatorações internas de baixo impacto
2. Decisões temporárias ("vamos usar Redis só pra testar")
3. Configurações triviais (linters, formatter, etc.)
4. Bugs, hotfixes, ajustes operacionais

### Observação

1. Podem ser justificadas em outros documentos
2. ADR serve para decisões duradouras.
3. Use documentação de engenharia.
4. Isso pertence a changelogs ou incident reports.


## Critérios objetivos (regra dos 3 E's)

Crie um ADR quando a decisão for:
1. Estrutural - afeta como o sistema é construído ou integrado
2. Evidente - outros desenvolvedores precisarão entender o porquê no futuro.
3. Estável - tende a durar meses ou anos, não semanas.







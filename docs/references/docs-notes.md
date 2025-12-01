## Tipos de documentação:

 - Produto - O que e por quê

*Desgin docs

- Design e Arquitetura - como
- Infra - onde e com o que
- Operacional - como manter
- Conhecimento e referência - como trabalhar

- PRD - Product Requirement DOcument

Níves:
- Produto
- Módulo / Epic
- Feature
- Etc.


## DOCUMENTOS COMUNS
- HLD - High Level Design - Como o sistema é estruturado
- FDD - Feature Design Doc - Como uma feature específica será implementada
- LLD - Low Level Design - Detalhes de implementação. ex: Contrato de uma API
- ADRs - Architecture Decision Record - Registram decisões arquiteturais ao longo de todo o processo
- RFCs - Request For Comments - Propõe o que será criado ou alterado (discussão de 'como' e coleta de

PRD > HLD
RFC > ADR


### HLD - High Level Design
- Como o sistema é estruturado?
- Quais componentes/módulos existem e como se comunicam?
- Quais tecnologias e padrões sendo adotados?

O que pode ser apresentado:

- Diagramas (ex: C4 nível 2: Container Diagram)
- Os Serviços, APIs e fluxos principais
- Padrões de comunicação (REST, gRPC, mensageria, MCP)
- Considerações de segurança, escalabilidade e disponibilidade

- HLD define o 'terreno' onde as features serão implementadas

#### Sections

- Objetivo
- Arquitetura geral
- Componentes e responsabilidades
- Fluxo de requisições
- Modelo de dados (alto nível)
- Interfaces públicas
- Considerações de escalabilidade
- Segurança
- Observabilidade
- Riscos

### Feature Design Doc - FDD

É o "como implementar uma feature específica" no contexto definido pelo HLD. Aqui vivem os contratos públicos reais, 0 comportamento exato, fluxos detalhados, erros, semântica de headers, opções de configuração via código, e critérios de aceite técnicos. É o documento que habilita a implementação sem ambiguidade.

Importante utilizar sempre que a feature expõe APIs, altera contratos, adiciona opções de configuração e tem efeitos claros em segurança, performance ou compatibilidade.

Responde perguntas como:
- Quais os principais detalhes técnicos dessa feature?
- Como essa feature se comporta em tempo de execução?
- Quais contratos e interfaces ela expõe para integração?
- Como ela é configurada e quais dependências exige?
- Como lida com erros, exceções e concorrência?
- Como validar que a implementação está correta e atende aos critérios técnicos?

#### Seções encontradas em um FDD 
- Contexto e motivação técnica
- Objetivos técnicos
- Escopo e exclusões
- Fluxos detalhados e diagramas
- Contratos públicos (assinaturas, endpoints, headers, exemplos)
- Erros. exceções e fallback
- Observabilidade
- Dependências de compatibilidade
- Critério de aceite técnicos
- Riscos e mitigação












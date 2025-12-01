## Diagramas C4

É um modelo para representar a arquitetura em diferentes níveis de detalhe. Ele organiza a visualização de como o sistema se relaciona com usuários e sistemas externos, quais containers o compõem, como cada parte interna é estruturada e, se necessário, como o código está organizado. Essa estrutura também facilita para

agentes de IA entenderem o contexto do sistema, permitindo análise, refatoração e geração de artefatos técnicos com mais precisão.

C1: System COntext (Visão Externa)
- Define o sistema no ambiente em que ele opera
- Identifica usuários, consumidores e integrações externas
- Bom para alinhamento entre diferentes times como: desenvolvimento, produto, segurança, etc.

C2: Container (arquitetura geral)
- Agrupa os principais blocos: serviços, aplicações, bancos, filas, APIs
- Evidencia como esses blocos se comunicam e em quais protocolos
- Ajuda em Decisões de infraestrutura, escalabilidade e deploy.

C3: Component (Estrutura interna)
- Organiza Cada Container em módulos, pacotes ou camadas
- Deixa Claro onde estão as responsabilidades
- Auxilia devs a manterem coesão e reduzirem acomplamento

C4: Code (Detalhe técnico - código)
- Aprofunda em classes, funções ou estruturas específicas
- Usado apenas quando há necessidade real de padronização ou aditoria
- Não é obrigatório na maioria dos projetos
- Raramente recomendado

## Diagramas Mermaid

Mermaid é uma linguagem de marcação que transforma texto em diagramas. Ela permite representar fluxos, interações e estruturas de sistemas de forma simples e legível dentro de documentos técnicos. Por gerar gráficos diretamente do código, facilita a manutenção, revisão e automação por agentes de IA, tornando a documentação sempre atualizada e consistente.

Flowchart (Fluxograma)
- Representa fluxos de decisão, etapas e caminhos alternativos
- Ideal para mostrar lógica de processos e pipelines
- útil em documentações de sistemas, APIs e automações

## Sequence Diagram (Diagrama de Sequência)
- Mostra a troca de mensagens entre componentes ao longo do tempo
- Excelente para visualizar chamadas entre serviços, APIs e bancos de dados
- Ajuda a identificar dependências e gargalos de comunicação

## Class Diagram (Diagrama de classe)
- Exibe classes, structs e seus relacionamentos
- Mostra atributos, métodos e heranças
- Bom para explicar a estrutura interna do código e o design do domínio

## ER Diagram (Entidade-Relacionamento)
- Exibe classes, structs e seus relacionamentos
- Mostra atributos, métodos e heranças
- Bom para explicar a estrutura interna do código e o design do domínio

## State Diagram (Diagrama de Estados)
- Mostra os estados possíveis de um sistema e suas transições
- Indicado para workflows, automações e máquinas de estado
- Ajuda a entender como o sistema reage a diferentes eventos e condições

---

## Resumo: Quando usar cada diagrama

### C4 (Foco em arquitetura)

| Nível | Caso de Uso |
|-------|-------------|
| C1 (System Context) | Visão externa - usuários, sistemas externos, integrações |
| C2 (Container) | Blocos de arquitetura - serviços, apps, DBs, filas, APIs, protocolos |
| C3 (Component) | Estrutura interna - módulos, pacotes, camadas, responsabilidades |
| C4 (Code) | Raramente usado - apenas para auditoria/padronização específica |

### Mermaid (Foco em fluxos/comportamento)

| Tipo | Caso de Uso |
|------|-------------|
| Flowchart | Fluxos de decisão, etapas, caminhos alternativos, lógica de processos |
| Sequence | Troca de mensagens, chamadas de API, interações entre serviços |
| Class | Classes, structs, atributos, métodos, herança, design de domínio |
| ER | Relacionamentos entre entidades, modelagem de dados |
| State | Estados e transições, workflows, máquinas de estado, reações a eventos |

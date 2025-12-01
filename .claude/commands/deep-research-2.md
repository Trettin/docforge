# Prompt para geração de uma Deep Research (Fase 2)

Você é um editor técnico e arquiteto de documentação.

O conteúdo completo da pesquisa já está disponível no contexto atual (não há necessidade de o usuário colar nada).

Sua tarefa é:

1. Ler **todos os conteúdos e documentos importados**.
2. **Reorganizar e reescrever** o texto conforme o modelo oficial de *Deep Research Document* descrito abaixo.
3. **Garantir que 100% das informações, frases, dados e explicações do texto original estejam presentes** no documento final, mesmo que seja necessário expandir ou duplicar trechos.
4. **Não eliminar, condensar ou omitir nada.**
5. Se algum trecho não se encaixar claramente em uma seção, inclua-o na seção mais relacionada e indique entre parênteses “(conteúdo contextual adicional)”.
6. O resultado deve ser entregue em **Markdown puro** para download ou nesse próprio chat.
7. NUNCA resuma absolutamente nada. 100% do conteúdo anexado deve constar, porém no formato do esqueleto abaixo, logo, pense passo a passo para garantir que isso seja possível. Ultrathink para fazer isso.

---

### Regras de execução

- Nenhum conteúdo pode ser perdido, resumido ou desconsiderado.
- Mantenha as 16 seções do esqueleto exatamente com os nomes fornecidos.
- Se o documento original tiver seções que não correspondem diretamente, redistribua o conteúdo dentro das mais adequadas, preservando integralmente o sentido.
- É permitido apenas melhorar clareza e coerência textual.
- Não realize “grounding” para o documento anexado, fazendo referencias a ele
- O documento final pode ser extenso: **não limite o tamanho**.
- Entregue apenas o Markdown final do *Deep Research Document*.

---

### Esqueleto oficial do Deep Research Document

# Deep Research Document

**Título:** [Tema técnico da pesquisa]

**Versão:** 1.0

**Data:** [Data atual]

**Responsável:** [Autor / IA / Time técnico]

## 1. Contexto e Motivação

Descreve o problema técnico, a oportunidade ou a motivação que originou a pesquisa, incluindo relevância e impacto.

## 2. Fundamentos e Conceitos-Chave

Apresenta princípios, teorias, modelos ou terminologias essenciais para compreender o tema.

## 3. Panorama e Abordagens Existentes

Analisa as abordagens predominantes, soluções conhecidas, padrões ou frameworks relacionados ao problema.

## 4. Arquiteturas e Modelos de Aplicação

Explica como o tema é aplicado em nível arquitetural, descrevendo topologias, camadas e fluxos de dados típicos.

## 5. Estratégias, Algoritmos e Mecanismos

Lista as principais estratégias, algoritmos e mecanismos que endereçam o problema, destacando diferenças e trade-offs.

## 6. Tecnologias, Frameworks e Ferramentas

Apresenta tecnologias, bibliotecas, protocolos ou frameworks relevantes, com comparação de maturidade e aplicabilidade.

## 7. Boas Práticas e Diretrizes Técnicas

Inclui recomendações de implementação, anti-patterns, práticas de governança e lições de engenharia.

## 8. Métricas e Critérios de Avaliação

Define como mensurar o sucesso técnico ou operacional, listando métricas e métodos de avaliação.

## 9. Casos de Uso e Aplicações Reais

Mostra exemplos de aplicação prática, estudos de caso ou referências de uso do tema no mercado.

## 10. Riscos, Desafios e Limitações

Descreve riscos, limitações técnicas, pontos de falha conhecidos e possíveis estratégias de mitigação.

## 11. Considerações de Segurança, Confiabilidade e Governança

Trata de aspectos de segurança, conformidade, privacidade, confiabilidade e versionamento.

## 12. Tendências e Evolução Futura

Apresenta tendências, inovações ou pesquisas emergentes relacionadas ao tema.

## 13. Impactos e Relações com o Ecossistema

Explica como o tema interage com outros sistemas, times, processos ou camadas de arquitetura.

## 14. Decisões e Oportunidades Técnicas (ADRs Candidatos)

Lista possíveis decisões técnicas ou arquiteturais derivadas da pesquisa, com critérios de escolha e alternativas rejeitadas.

## 15. Próximos Passos e Aplicação Prática

Propõe como aplicar os aprendizados em produtos, sistemas, pipelines ou processos futuros.

## 16. Referências e Leituras Recomendadas

Apresenta todas as fontes utilizadas: artigos, papers, RFCs, whitepapers, documentações e materiais técnicos.

---

### Instrução final

- Garanta que a integral do conteúdo da pesquisa já importada no contexto. (Pode ser um PDF, docs, md, etc).
- Não faça a separação do documento em páginas, ou seja, jamais coloque algo como: Página 1, Página 2, etc.
- Reestruture-a completamente de acordo com o *Deep Research Document* acima, **garantindo que 100% do material original esteja presente** no resultado final, ainda que o documento se torne extremamente grande. Não realize grounding, e pense passo a passo como garantir e certificar que 100% do conteúdo foi adicionado ao documento final.
- Não realize NENHUMA sumarização ou resumo de qualquer natureza. Não faça apontamentos ou grounding nesse documento para o conteúdo anexado que você está utilizando como contexto.
- Garanta que o documento seja extremamente bem formatado com seus títulos, subtítulos, entre outros, baseado no esqueleto fornecido.
- Entregue apenas o Markdown final completo, sem explicações adicionais.
- Caso os documentos anexados sejam muito grandes, você poderá optar por gerar o Deep Research Document em fases. Ex: Gerar primeiramente das seções 1 a 4, depois 5 a 9 e assim por diante. Caso queira fazer dessa forma, informe o usuário dizendo que você iniciará da Seção 1 até 3, assim que você trouxer as seções geradas, pergunte se ele deseja continuar gerando agora da seção 4 a 7, e assim por diante.

---

## Regras de Localização do Arquivo

Após formatar a pesquisa, salve o resultado no mesmo diretório do arquivo da Fase 1:

- **Nível de projeto:** `docs/project/research/RESEARCH-RESULT-[topico].md`
- **Nível de feature:** `docs/features/[nome-da-feature]/research/RESEARCH-RESULT-[topico].md`

A Fase 1 gera `RESEARCH-[topico].md` e a Fase 2 gera `RESEARCH-RESULT-[topico].md`.

---

## Após Salvar a Pesquisa

Após salvar o resultado da pesquisa com sucesso:

1. **Atualize `docs/PROGRESS.md`**:
   - Marque o passo do Deep Research Fase 2 como completado com `[x]`
   - Adicione `◄── VOCÊ ESTÁ AQUI` no próximo passo
   - Atualize o timestamp de `Last Updated`
   - Atualize o número de `Current Step`

2. **Mostre o resumo de progresso e sugira próximos passos** (diferenciando projeto vs feature):

   **Se nível de projeto:**

   Analise a pesquisa e identifique possíveis ADRs a serem criadas:
   ```
   ---
   Progresso: [X/Y] documentos completados

   Completados:
   - [x] PRD
   - [x] User Stories
   - [x] HLD
   - [x] Diagramas (C4/Mermaid)
   - [x] Deep Research (Fase 1 e 2)

   **Importante:** Leia os achados da pesquisa antes de prosseguir. Eles serão fundamentais para as próximas etapas.

   Com base na pesquisa, as seguintes ADRs podem ser relevantes:
   - ADR-XXXX: [título sugerido baseado em decisão identificada]
   - ADR-XXXX: [título sugerido baseado em decisão identificada]

   Próximo passo: Execute `/clear` para limpar o contexto, depois `/adr-create` para cada ADR.
   ---
   ```

   **Se nível de feature:**

   Direcione o usuário para criar o FDD da feature atual:
   ```
   ---
   Progresso: [X/Y] documentos completados

   Completados:
   - [x] PRD (feature)
   - [x] User Stories (feature)
   - [x] Deep Research (Fase 1 e 2)

   **Importante:** Leia os achados da pesquisa antes de prosseguir. Eles serão fundamentais para as próximas etapas.

   A pesquisa foi concluída! Agora você tem o contexto necessário para criar o FDD.

   Próximo passo: Execute `/clear` para limpar o contexto, depois `/fdd-create docs/features/[nome-da-feature]/PRD.md`
   ---
   ```
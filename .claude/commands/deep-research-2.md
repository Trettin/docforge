# Prompt for Deep Research Generation (Phase 2)

You are a technical editor and documentation architect.

The complete research content is already available in the current context (there is no need for the user to paste anything).

Your task is:

1. Read **all imported content and documents**.
2. **Reorganize and rewrite** the text according to the official *Deep Research Document* template described below.
3. **Ensure that 100% of the information, sentences, data, and explanations from the original text are present** in the final document, even if it is necessary to expand or duplicate sections.
4. **Do not eliminate, condense, or omit anything.**
5. If any section does not clearly fit into a category, include it in the most related section and indicate "(additional contextual content)" in parentheses.
6. The result must be delivered in **pure Markdown** for download or in this chat.
7. NEVER summarize absolutely anything. 100% of the attached content must be included, but in the format of the skeleton below, so think step by step to ensure this is possible. Ultrathink to accomplish this.

---

### Execution Rules

- No content can be lost, summarized, or disregarded.
- Maintain the 16 sections of the skeleton exactly with the names provided.
- If the original document has sections that do not correspond directly, redistribute the content within the most appropriate ones, fully preserving the meaning.
- Only improvements to textual clarity and coherence are allowed.
- Do not perform "grounding" for the attached document by making references to it.
- The final document can be extensive: **do not limit the size**.
- Deliver only the final Markdown of the *Deep Research Document*.

---

### Official Deep Research Document Skeleton

# Deep Research Document

**Title:** [Technical research topic]

**Version:** 1.0

**Date:** [Current date]

**Author:** [Author / AI / Technical team]

## 1. Context and Motivation

Describes the technical problem, opportunity, or motivation that originated the research, including relevance and impact.

## 2. Fundamentals and Key Concepts

Presents principles, theories, models, or essential terminologies for understanding the topic.

## 3. Landscape and Existing Approaches

Analyzes predominant approaches, known solutions, patterns, or frameworks related to the problem.

## 4. Architectures and Application Models

Explains how the topic is applied at an architectural level, describing typical topologies, layers, and data flows.

## 5. Strategies, Algorithms, and Mechanisms

Lists the main strategies, algorithms, and mechanisms that address the problem, highlighting differences and trade-offs.

## 6. Technologies, Frameworks, and Tools

Presents relevant technologies, libraries, protocols, or frameworks, with comparison of maturity and applicability.

## 7. Best Practices and Technical Guidelines

Includes implementation recommendations, anti-patterns, governance practices, and engineering lessons.

## 8. Metrics and Evaluation Criteria

Defines how to measure technical or operational success, listing metrics and evaluation methods.

## 9. Use Cases and Real-World Applications

Shows examples of practical application, case studies, or references of topic usage in the market.

## 10. Risks, Challenges, and Limitations

Describes risks, technical limitations, known failure points, and possible mitigation strategies.

## 11. Security, Reliability, and Governance Considerations

Addresses security aspects, compliance, privacy, reliability, and versioning.

## 12. Trends and Future Evolution

Presents trends, innovations, or emerging research related to the topic.

## 13. Impacts and Ecosystem Relationships

Explains how the topic interacts with other systems, teams, processes, or architecture layers.

## 14. Decisions and Technical Opportunities (Candidate ADRs)

Lists possible technical or architectural decisions derived from the research, with selection criteria and rejected alternatives.

## 15. Next Steps and Practical Application

Proposes how to apply the learnings in future products, systems, pipelines, or processes.

## 16. References and Recommended Reading

Presents all sources used: articles, papers, RFCs, whitepapers, documentation, and technical materials.

---

### Final Instruction

- Ensure the entirety of the research content already imported in the context. (Can be a PDF, docs, md, etc).
- Do not separate the document into pages, meaning never put something like: Page 1, Page 2, etc.
- Completely restructure it according to the *Deep Research Document* above, **ensuring that 100% of the original material is present** in the final result, even if the document becomes extremely large. Do not perform grounding, and think step by step how to ensure and verify that 100% of the content was added to the final document.
- Do not perform ANY summarization of any kind. Do not make notes or grounding in this document to the attached content you are using as context.
- Ensure the document is extremely well formatted with its titles, subtitles, and others, based on the skeleton provided.
- Deliver only the complete final Markdown, without additional explanations.
- If the attached documents are very large, you may choose to generate the Deep Research Document in phases. Ex: First generate sections 1 to 4, then 5 to 9 and so on. If you want to do it this way, inform the user by saying that you will start from Section 1 to 3, once you bring the generated sections, ask if they want to continue generating now from section 4 to 7, and so on.

---

## File Location Rules

After formatting the research, save the result in the same directory as the Phase 1 file:

- **Project level:** `docs/project/research/RESEARCH-RESULT-[topic].md`
- **Feature level:** `docs/features/[feature-name]/research/RESEARCH-RESULT-[topic].md`

Phase 1 generates `RESEARCH-[topic].md` and Phase 2 generates `RESEARCH-RESULT-[topic].md`.

---

## After Saving the Research

After successfully saving the research result:

1. **Update `docs/PROGRESS.md`**:
   - Mark the Deep Research Phase 2 step as completed with `[x]`
   - Add `◄── YOU ARE HERE` to the next step
   - Update the `Last Updated` timestamp
   - Update the `Current Step` number

2. **Show progress summary and suggest next steps** (differentiating project vs feature):

   **If project level:**

   Analyze the research and identify possible ADRs to be created:
   ```
   ---
   Progress: [X/Y] documents completed

   Completed:
   - [x] PRD
   - [x] User Stories
   - [x] HLD
   - [x] Diagrams (C4/Mermaid)
   - [x] Deep Research (Phase 1 and 2)

   **Important:** Read the research findings before proceeding. They will be essential for the next steps.

   Based on the research, the following ADRs may be relevant:
   - ADR-XXXX: [suggested title based on identified decision]
   - ADR-XXXX: [suggested title based on identified decision]

   Next step: Run `/clear` to clear context, then `/adr-create` for each ADR.
   ---
   ```

   **If feature level:**

   Direct the user to create the FDD for the current feature:
   ```
   ---
   Progress: [X/Y] documents completed

   Completed:
   - [x] PRD (feature)
   - [x] User Stories (feature)
   - [x] Deep Research (Phase 1 and 2)

   **Important:** Read the research findings before proceeding. They will be essential for the next steps.

   Research completed! Now you have the context needed to create the FDD.

   Next step: Run `/clear` to clear context, then `/fdd-create docs/features/[feature-name]/PRD.md`
   ---
   ```

---
description: Generate C4 diagrams from a Feature Design Document (FDD). Usage: /generate-c4 <path-to-fdd.md> [output-folder] [--no-images]
---

You MUST invoke the c4-diagram-generator agent using the Task tool with subagent_type="c4-diagram-generator".

Extract the FDD file path, output folder, and optional --no-images flag from the command arguments:
- FDD file path (required)
- Output folder (required)
- --no-images flag (optional, if present: skip PNG generation, if absent: generate PNG images by default)

Pass the following prompt to the agent:

"Generate C4 diagrams from the Feature Design Document located at [FDD_FILE_PATH].

Output folder: [OUTPUT_FOLDER]
PNG generation: [PNG_INSTRUCTION]

Execute your complete workflow (Phases 1-6) following all internal guidelines.

CRITICAL REMINDERS:
- Create separate .puml files using Write tool for EACH diagram (c1, c2, c3, c4) - this is MANDATORY
- Create ONE .md file with analysis ONLY (NO PlantUML code inside)
- Only generate diagrams with sufficient FDD information - never fabricate
- [PNG_BEHAVIOR]

REPORT must include:
- Detected language of FDD
- Explicit list of ALL created files (.puml, .md, and .png if applicable)
- Number of diagrams generated with brief justification
- Skipped diagrams with specific reasons
- Verification: 'Created N .puml files for N diagrams'
- PNG generation results (if applicable)"

Replace [FDD_FILE_PATH] with the actual file path from command arguments.
Replace [OUTPUT_FOLDER] with the specified output folder from command arguments.
Replace [feature-name] with the appropriate feature name extracted from the FDD filename.

Replace [PNG_INSTRUCTION] and [PNG_BEHAVIOR] based on --no-images flag:

If --no-images flag IS present:
- [PNG_INSTRUCTION] = "DISABLED"
- [PNG_BEHAVIOR] = "Skip PNG generation (Phase 5.6) entirely"

If --no-images flag IS NOT present (default):
- [PNG_INSTRUCTION] = "ENABLED"
- [PNG_BEHAVIOR] = "Execute Phase 5.6: Generate PNG images with automatic error correction (max 3 attempts per file)"

---

## After Generating C4 Diagrams

After successfully generating the diagrams:

1. **Update `docs/PROGRESS.md`**:
   - Mark the C4 Diagrams step as completed with `[x]`
   - Add `◄── YOU ARE HERE` to the next step
   - Update the `Last Updated` timestamp
   - Update the `Current Step` number

2. **Determine next steps based on context** (project vs feature):

   **If project level** (source file is `docs/project/HLD.md`):
   ```
   ---
   Progress: [X/Y] documents completed

   Completed:
   - [x] PRD
   - [x] User Stories
   - [x] HLD
   - [x] C4 Diagrams

   **Important:** Review the generated C4 diagrams before proceeding. Verify that they correctly represent the system architecture.

   Next step: Run `/clear` to clear context, then:
   - If you haven't generated Mermaid diagrams yet: `/mermaid-diagram-create docs/project/HLD.md docs/project/diagrams/`
   - If deep research is needed: `/deep-research-1`
   - If there are architectural decisions to document: `/adr-create`
   ---
   ```

   **If feature level** (source file is `docs/features/[name]/FDD.md`):
   ```
   ---
   Progress: [X/Y] documents completed

   Completed:
   - [x] PRD
   - [x] User Stories
   - [x] FDD
   - [x] C4 Diagrams

   **Important:** Review the generated C4 diagrams before proceeding. Verify that they correctly represent the feature architecture.

   Next step: Run `/clear` to clear context, then:
   - If you haven't generated Mermaid diagrams yet: `/mermaid-diagram-create docs/features/[name]/FDD.md docs/features/[name]/diagrams/`
   - If there are architectural decisions to document: `/adr-create`
   ---
   ```
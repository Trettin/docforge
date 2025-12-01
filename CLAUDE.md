# CLAUDE.md

This file provides guidance to Claude Code when working with this repository.

## Project Overview

This is a Software Documentation Framework - a boilerplate repository that helps developers create proper documentation before starting to code. Users interact with Claude Code by running slash commands in sequence.

## Main Files and Folders

- `docs/PROGRESS.md` - Tracks user progress in the documentation flow. Update after each document is created.
- `docs/ADRs.md` - Global index of all ADRs. Check here for the next ADR number.
- `docs/project/` - Project-level documentation (PRD, HLD, User Stories, ADRs, research)
- `docs/features/` - Feature-level documentation, organized by feature name
- `.claude/commands/` - Slash command definitions for document creation
- `.claude/agents/` - Agent definitions for diagram generation

## Available Commands

| Command | Creates |
|---------|---------|
| `/prd-create` | PRD (Product Requirements Document) |
| `/user-stories-create` | User Stories with BDD acceptance criteria |
| `/hld-create` | HLD (High Level Design) |
| `/fdd-create` | FDD (Feature Design Document) |
| `/adr-create` | ADR (Architecture Decision Record) |
| `/deep-research-1` | Deep research phase 1 |
| `/deep-research-2` | Deep research phase 2 |
| `/c4-diagram-create` | C4 architecture diagrams |
| `/mermaid-diagram-create` | Mermaid diagrams |

## Document Flow

### New Project
1. `/prd-create` → `docs/project/PRD.md`
2. `/user-stories-create` → `docs/project/USER-STORIES.md`
3. `/hld-create` → `docs/project/HLD.md`
4. `/c4-diagram-create` + `/mermaid-diagram-create` → `docs/project/c4/` and `docs/project/diagrams/`
5. `/deep-research-1` + `/deep-research-2` → `docs/project/research/` *(optional, but if you start phase 1, complete phase 2)*
6. `/adr-create` (repeat as needed) → `docs/project/adrs/`

### New Feature
1. `/prd-create` → `docs/features/[name]/PRD.md`
2. `/user-stories-create` → `docs/features/[name]/USER-STORIES.md`
3. `/deep-research-1` + `/deep-research-2` → `docs/features/[name]/research/` *(optional, but if you start phase 1, complete phase 2)*
4. `/fdd-create` → `docs/features/[name]/FDD.md`
5. `/c4-diagram-create` + `/mermaid-diagram-create` → `docs/features/[name]/diagrams/`
6. `/adr-create` (if needed) → `docs/features/[name]/adrs/`

## After Creating a Document

After successfully creating a document:

1. **Update `docs/PROGRESS.md`**:
   - Mark the completed step with `[x]`
   - Add `◄── YOU ARE HERE` to the next step
   - Update the `Last Updated` timestamp
   - Update the `Current Step` number

2. **Show the progress summary** to the user:
   ```
   ---
   Progress: [X/Y] documents completed

   Completed:
   - [x] PRD
   - [x] User Stories

   Next step: Run `/clear` to clear context, then run `/hld-create`
   ---
   ```

3. **If creating an ADR**, also update `docs/ADRs.md`:
   - Add entry to the table with all metadata
   - ADR numbers are global/sequential across the entire project

## ADR Numbering

ADRs use global sequential numbering regardless of where they are located:
- `docs/project/adrs/ADR-0001-*.md`
- `docs/features/login/adrs/ADR-0002-*.md`
- `docs/features/payments/adrs/ADR-0003-*.md`

Before creating a new ADR, check `docs/ADRs.md` to determine the next number.

## File Location Rules

| Document Type | Project Level | Feature Level |
|---------------|---------------|---------------|
| PRD | `docs/project/PRD.md` | `docs/features/[name]/PRD.md` |
| User Stories | `docs/project/USER-STORIES.md` | `docs/features/[name]/USER-STORIES.md` |
| HLD | `docs/project/HLD.md` | N/A (HLD is always project level) |
| FDD | N/A (FDD is always feature level) | `docs/features/[name]/FDD.md` |
| ADRs | `docs/project/adrs/ADR-XXXX-*.md` | `docs/features/[name]/adrs/ADR-XXXX-*.md` |
| Research | `docs/project/research/` | `docs/features/[name]/research/` |
| C4 Diagrams | `docs/project/c4/` | `docs/features/[name]/c4/` |
| Mermaid Diagrams | `docs/project/diagrams/` | `docs/features/[name]/diagrams/` |

## Creating Feature Folders

When creating documentation for a new feature:

1. Ask the user for the feature name
2. Create the folder structure:
   ```
   docs/features/[feature-name]/
   ├── adrs/
   ├── research/
   ├── c4/
   └── diagrams/
   ```
3. Place documents in the appropriate locations

## Language

- All commands and templates are in English
- JSON exports use English keys with English values
- README and CLAUDE.md are in English (except technical terms)

## Style Guidelines

- Use simple and direct English
- One question at a time during interviews
- Summarize and confirm before proceeding
- Do not use em dashes like "—"
- Mark assumptions as "hypothesis"

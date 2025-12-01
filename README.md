# Software Documentation Framework

![Version](https://img.shields.io/badge/version-0.1.0-blue)
![License](https://img.shields.io/badge/license-MIT-green)
![Language](https://img.shields.io/badge/lang-en-yellow)
![Claude Code](https://img.shields.io/badge/Claude%20Code-compatible-orange)
[![pt-BR](https://img.shields.io/badge/lang-pt--BR-green)](../../tree/feat/pt-br)

A framework to help developers start new projects with proper documentation through an AI-assisted interactive workflow.

## What is this?

This repository provides a structured flow to create software documentation **before** coding. You interact with an AI agent (Claude Code) by running commands in sequence, and by the end you'll have all the essential documents to start development.

## Why?

Design documentation is not bureaucracy. It's the difference between building something that works and building something that solves the right problem.

**For traditional development:**
- Reduces rework by aligning expectations before writing code
- Facilitates onboarding of new team members
- Creates a historical record of technical decisions (ADRs)
- Forces you to think about edge cases before encountering them in production

**For AI agent development:**
- AI agents are excellent executors, but they need clear context
- Without documentation, the agent "guesses" requirements and architecture
- With documentation, the agent has an explicit contract of what to build
- PRDs and FDDs function as high-quality structured prompts
- User Stories with BDD criteria become verifiable tests
- The agent can reference ADRs to maintain architectural consistency

**The speed paradox:**
It seems faster to jump straight into code. But without clear documentation, you spend more time fixing misunderstandings, refactoring bad decisions, and explaining the system repeatedly. With AI agents, this problem is amplified: the agent works fast, but in the wrong direction.

Investing 30 minutes in documentation can save hours of rework.

## Quick Start

1. Clone this repository
2. Open in terminal with Claude Code
3. Run `/prd-create` to get started

## Documentation Flow

### New Project (Full Flow)

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
                              /deep-research-1 + /deep-research-2 (optional)
                                              │
                                              ▼
                                        /adr-create (×N)
                                              │
                                              ▼
                                    docs/project/adrs/
```

### New Feature (Feature Flow)

```
/prd-create ──► /user-stories-create ──► /deep-research-1 + /deep-research-2 (optional*)
(feature)              │                              │
     │                 ▼                              ▼
docs/features/   docs/features/                 docs/features/
[name]/PRD.md    [name]/USER-STORIES.md         [name]/research/
                                                      │
                                                      ▼
                                                /fdd-create
                                                      │
                                                      ▼
                                            docs/features/[name]/FDD.md
                                                      │
                                                      ▼
                              /c4-diagram-create + /mermaid-diagram-create
                                                      │
                                                      ▼
                                        docs/features/[name]/diagrams/

* optional, but if you start phase 1, complete phase 2
```

## Available Commands

| Command | Purpose | Output |
|---------|---------|--------|
| `/prd-create` | Create Product Requirements Document | PRD.md |
| `/user-stories-create` | Create User Stories with BDD acceptance criteria | USER-STORIES.md |
| `/hld-create` | Create High Level Design | HLD.md |
| `/fdd-create` | Create Feature Design Document | FDD.md |
| `/adr-create` | Create Architecture Decision Record | ADR-XXXX.md |
| `/deep-research-1` | Deep research phase 1 | Research context |
| `/deep-research-2` | Deep research phase 2 | RESEARCH-[topic].md |
| `/c4-diagram-create` | Create C4 architecture diagrams | .puml files |
| `/mermaid-diagram-create` | Create Mermaid diagrams | diagrams.md |

## Document Types

| Document | Level | Purpose |
|----------|-------|---------|
| **PRD** | Project or Feature | WHY and WHAT - business requirements, scope, metrics |
| **User Stories** | Project or Feature | WHO wants WHAT - user behaviors with acceptance criteria |
| **HLD** | Project | HOW (high level) - system architecture, components |
| **FDD** | Feature | HOW (detailed) - technical implementation details |
| **ADR** | Project or Feature | WHY this decision - architectural decisions with trade-offs |

## Folder Structure

```
docs/
├── PROGRESS.md          # Tracks your progress in the documentation flow
├── ADRs.md              # Index of all ADRs with metadata
├── docs-notes.md        # Reference material about documentation types
│
├── project/             # Project-level documents
│   ├── PRD.md
│   ├── USER-STORIES.md
│   ├── HLD.md
│   ├── research/        # Deep research outputs
│   ├── adrs/            # Project-level ADRs
│   ├── c4/              # Project C4 diagrams
│   └── diagrams/        # Project Mermaid diagrams
│
└── features/            # Feature-level documents
    └── [feature-name]/
        ├── PRD.md
        ├── USER-STORIES.md
        ├── FDD.md
        ├── research/    # Feature research (if needed)
        ├── adrs/        # Feature-specific ADRs
        ├── c4/          # C4 diagrams
        └── diagrams/    # Mermaid diagrams
```

## Workflow Tips

1. **After each command**, the AI will show your progress and indicate the next step
2. **Run `/clear`** between commands to clear context and start fresh
3. **Check `docs/PROGRESS.md`** to see where you are in the flow
4. **ADRs are numbered globally** - check `docs/ADRs.md` for the current number

## Creating a New Project vs New Feature

### New Project
Start with `/prd-create` and follow the full flow. This creates system-level documentation in `docs/project/`.

### New Feature
Start with `/prd-create` for the feature. When asked, specify that it's for an existing system. Documents go to `docs/features/[feature-name]/`.

## References

- [C4 Model](https://c4model.com/)
- [MADR - Markdown ADRs](https://adr.github.io/madr/)
- [Mermaid Docs](https://mermaid.js.org/)

---

## Support

If this framework helped you write better documentation, consider giving it a ⭐ — it helps others discover the project!

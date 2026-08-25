# GPT-Knowledge

Central knowledge base for projects, technical systems, workflows, decisions, and reusable context used across ChatGPT-assisted work.

## Purpose

This repository is the canonical, human-readable project knowledge base. It is intended to preserve useful context between sessions and make project information structured, searchable, and maintainable.

## Knowledge Architecture

```text
GPT-Knowledge/
├── INDEX.md                 # Master navigation and knowledge map
├── CHANGELOG.md             # Important knowledge-base changes
├── projects/                # Project-specific knowledge
│   ├── README.md
│   └── <project>/
├── systems/                 # Devices, OS, infrastructure, networking, AI stack
│   ├── README.md
│   └── <system>/
├── workflows/               # Repeatable procedures and automation workflows
│   ├── README.md
│   └── <workflow>.md
├── decisions/               # Important technical/product decisions and rationale
│   ├── README.md
│   └── <decision>.md
├── research/                # Research notes, comparisons, findings
│   ├── README.md
│   └── <topic>.md
├── references/              # Useful commands, configuration references, links
│   ├── README.md
│   └── <topic>.md
└── archive/                 # Superseded information retained for historical context
```

## Operating Rules

1. `INDEX.md` is the first place to look for knowledge.
2. Keep project knowledge inside `projects/` rather than mixing it into general notes.
3. Record durable technical decisions in `decisions/` with the date, decision, alternatives considered, and rationale.
4. Record repeatable procedures in `workflows/` so they can be reused without reconstructing the process from chat history.
5. Update existing documents instead of creating duplicate notes when the information belongs to an existing topic.
6. Mark obsolete information clearly and move genuinely superseded material to `archive/` when appropriate.
7. Prefer concise Markdown, explicit dates (`YYYY-MM-DD`), and stable filenames.
8. Do not store passwords, API keys, tokens, private keys, financial account credentials, identity documents, or other secrets in this repository.
9. Because this repository is public, do not place sensitive personal information or confidential third-party/client information here.
10. Never treat this repository as a secret store. Secrets belong in an appropriate password manager, environment-variable store, or secret-management system.

## Maintenance Convention

When a durable project fact, architecture decision, workflow, configuration, or research finding is established during a session, it should be reflected in this repository when explicitly requested or when the work is being maintained through the repository.

Each project should ideally contain:

- `README.md` — project overview and current status
- `ARCHITECTURE.md` — system architecture and integrations
- `ROADMAP.md` — planned work
- `DECISIONS.md` — project-specific decisions
- `CHANGELOG.md` — significant changes

## Current Repository Status

This knowledge base was initialized on 2026-08-26. The repository is currently being structured for ongoing use.

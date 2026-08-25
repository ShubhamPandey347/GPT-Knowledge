# GPT-Knowledge — Master Index

**Last initialized:** 2026-08-26  
**Repository:** `ShubhamPandey347/GPT-Knowledge`  
**Branch:** `main`

This is the master navigation page for the knowledge base. It should remain concise and point to the canonical document for each area.

---

## 1. Projects

Project-specific requirements, architecture, implementation status, deployment details, and roadmaps.

- [`projects/`](projects/) — all projects
- Project entries should be added here as they are created.

### Known project areas

- AI automation / agency work
- Cosmic Doctor SaaS / CRM
- SmartTap NFC business card
- Local AI / agent infrastructure
- Other software and automation projects as they become active

---

## 2. Systems & Infrastructure

Technical environment information that is useful across projects.

- [`systems/`](systems/) — devices, operating systems, networking, storage, AI infrastructure
- Hardware and OS configurations
- Local LLM stack (Ollama / LM Studio / related tooling)
- Docker, WSL, Linux and Windows environments
- Networking, remote access and tunnels
- Storage, synchronization and backup architecture

---

## 3. Workflows

Repeatable procedures that should not need to be reconstructed from conversation history.

- [`workflows/`](workflows/) — operational and technical workflows
- Backup / restore procedures
- Media processing and transcription pipelines
- Deployment procedures
- AI-agent setup procedures
- Data synchronization procedures

---

## 4. Decisions

Durable decisions and their rationale.

- [`decisions/`](decisions/) — architecture, tooling, product and workflow decisions
- Prefer one document per meaningful decision.
- Include date, context, decision, alternatives, rationale, consequences, and status.

---

## 5. Research

Research notes and comparisons that may inform future decisions.

- [`research/`](research/) — technical research, product comparisons, feasibility studies, and findings

---

## 6. References

Reusable commands, configuration references, external documentation links, and concise technical cheat sheets.

- [`references/`](references/) — reusable technical references

---

## 7. Archive

Superseded information retained for historical context.

- [`archive/`](archive/) — obsolete or replaced knowledge

---

## Knowledge Lifecycle

```text
Conversation / Experiment
        ↓
Useful durable information identified
        ↓
Classify
  ├── Project      → projects/
  ├── System       → systems/
  ├── Workflow     → workflows/
  ├── Decision     → decisions/
  ├── Research     → research/
  └── Reference    → references/
        ↓
Update canonical document
        ↓
Update INDEX.md when navigation changes
        ↓
Record significant changes in CHANGELOG.md
```

## Source-of-Truth Rules

- **Current implementation:** project documentation and repository code.
- **System state:** the relevant document under `systems/`.
- **Why a decision was made:** `decisions/`.
- **How to repeat a process:** `workflows/`.
- **What was discovered:** `research/`.
- **Historical/superseded information:** `archive/`.

When two documents conflict, the newer explicitly dated document wins unless it is marked historical or superseded.

## Security Boundary

This repository is public. Never put secrets or sensitive data here, including:

- API keys, access tokens, passwords, private keys
- Banking/payment credentials
- Identity-document details
- Sensitive personal information
- Confidential client/customer information
- Private infrastructure credentials

Use placeholders such as `<API_KEY>` or `<DOMAIN>` where configuration examples are needed.

## Update Convention

For future repository maintenance, prefer:

1. Inspect the existing index and relevant canonical document.
2. Update the existing document when possible.
3. Create a new document only when the topic is genuinely new.
4. Update this index if a new top-level topic or project is introduced.
5. Add a concise entry to `CHANGELOG.md` for significant knowledge changes.

The repository is intended to be a **living knowledge base**, not a raw transcript dump. Store durable facts, decisions, architecture, workflows, and useful distilled context rather than entire conversations.

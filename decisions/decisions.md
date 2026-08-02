# Decisions

Version: 1.0
Status: Official
Owner: Company OS

---

## Purpose

The Decisions log records every decision that shapes Company OS.

A decision is recorded with its date, its context, and its consequences.

The repository is the single source of truth for the project.

---

## Decision Log

### D-2026-07-04 — The Project Has a Name

**Status:** Accepted

The research on knowledge and cognition receives a permanent name: Company OS.

The project will be treated as an engineering discipline, not as a collection of conversations.

---

### D-2026-07-05 — From Definitions to the Lexicon

**Status:** Accepted

The first cognitive concepts are defined (Observation, Evidence, Context).

The Cognitive Lexicon is introduced as the shared vocabulary of the project.

---

### D-2026-07-06 — The Lexicon Becomes a System

**Status:** Accepted

The Lexicon stops being a glossary and becomes a cognitive system.

The Ontology is introduced as the map of the cognitive universe.

The first draft of the Seven Cognitive Principles is produced.

Rules adopted:

- The Ontology evolves gradually.
- Principles become Official only after validation.
- Core Concepts describe cognition, not software.
- Every new concept must belong to a cognitive family.

---

### D-2026-07-07 — The Template Is Frozen

**Status:** Accepted

Cognitive Concept Template v1.0 is declared Official.

The template is considered stable for version 1.x.

Every Core Concept will implement a Cognitive Contract.

The repository becomes the single source of truth.

The `state/` directory is introduced so the project can continue independently of any conversation.

---

### D-2026-07-31 — Lexicon Completion

**Status:** Accepted

The ten Core Concepts are completed and declared Official.

Cognitive Principles and Cognitive Families are formalized and declared Official.

The Cognitive Lexicon reaches version 1.0.

The architecture phase begins: translating cognitive contracts into computational components.

---

## Directive 001 — Recovery First

**Status:** Recorded

Origin: Conversation recovery, July 2026.

```
Research is suspended.
Recovery has priority over discovery.
No new architectural concepts until canonical state is recovered.
```

**Consequence:** The canonical state was reconstructed from the repository and its history. The Lexicon was completed from that recovered state.

---

## Directive 002 — Journaling at the Point of Change

**Status:** Recorded

Origin: Journal cadence revision, August 2026.

```
Trigger (operational definition):
A journal entry is required for every session that ends having created,
modified, or deleted any file of the canonical state.

Canonical state = every file under the repository root, excluding
journal entries and this directive.

Entry content: the established format (Theme, Progress, Discoveries,
Decisions, Reflection, Quote of the Day), and it must list the files
that changed.

Date: the day the session closes (the day of the last change).

No entry is required for read-only sessions, or for sessions that only
modify the journal itself.

Verification (decidable): compliance is checked by comparing the
canonical state at the start and end of a session. A canonical change
without a journal entry is an anomaly and must be recorded.
```

**Consequence:** A canonical change without a journal entry is considered unrecovered (E6, E4). The recovery procedure in `state/project-state.md` must close the gap before continuing.

---

## How to Record a Decision

Every new decision must include:

- Date
- Status (Accepted, Proposed, Rejected, Superseded)
- Context
- Decision
- Consequences

Major architectural decisions should also be documented as an ADR in `adr/`.

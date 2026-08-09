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

> Addendum (2026-08-02): "Principles become Official only after validation" is clarified. Official status means a principle is formalized and accepted into the canon as a hypothesis; validation is a separate, later phase (Phase 4). A principle becomes a law only after it survives confrontation with experience (see cognitive-principles.md, "Status of the Principles").

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

### D-2026-08-07 — SAP R/3 Integration Is an External, Non-Canonical Capability

**Status:** Accepted

**Context:** The implementation repository `company-os-monitor` needs to post
downtime costs and weighted metrics to SAP R/3 (ECC) for a datacenter
observability platform. No cognitive concept covers this integration; the canon
contains no decision about it. Per E2 ("A component that does not map to a
concept has no place in the system") and R9 ("The architecture guides the code,
never the opposite"), the integration must not be treated as a cognitive
component of the architecture.

**Decision:** The SAP R/3 integration is an external, non-canonical capability
of `company-os-monitor`. It is not a cognitive concept, is not part of the
Cognitive Lexicon, and does not alter the canonical flow. It is implemented as
an interchangeable gateway:

- Transport: RFC/BAPI via PyRFC (SAP NW RFC SDK), optional dependency.
- Downtime cost: `cost = hours_down * rate_per_hour` (asset/service rate).
- Posting: `BAPI_ACC_ACTIVITY_ALLOC_POST` (activity allocation) and
  `BAPI_ACC_DOCUMENT_POST`; always `BAPI_TRANSACTION_COMMIT` after success and
  `BAPI_TRANSACTION_ROLLBACK` on error.
- Weighted metrics: sent with per-asset/service weights.
- A mock mode is provided for development and tests; it must never be enabled
  in production.

**Consequences:**

- E2 holds: the capability is external; it does not claim a concept slot.
- R9 holds: the architecture guides the code; the integration adapts to the
  canon, not the other way around.
- Traceability: any future change to the SAP capability is documented here or
  in an ADR/RFC before the code changes.
- The first implementation of this decision lives in `company-os-monitor`.

---

### D-2026-08-09 — COS-Monitor Expands into a Product; External Capabilities Follow a Product Blueprint

**Status:** Accepted

**Context:** The implementation repository `company-os-monitor` currently
implements the cognitive flow of Company OS (Reality → Decision) as a
one-shot pipeline, plus the SAP R/3 external capability (D-2026-08-07). A
product blueprint now specifies the surrounding datacenter-observability
product: telemetry agents (Linux/Windows/VMware/network), a web dashboard,
threshold alerts, executive PDF reports, multi-tenant authentication, and
local LLM analysis (LM Studio, OpenAI-compatible). None of these map to a
cognitive concept. Per E2 and R9, they cannot be treated as cognitive
components of the architecture.

**Decision:** `company-os-monitor` keeps its name and becomes the product. The
cognitive core (the canonical flow in `app/`) is the brain; everything else
(agents, API, dashboard, alerts, reports, authentication, LLM client) is an
external, non-canonical product capability. The product blueprint is a
specification document, not a concept; it does not alter the canonical flow
and does not enter the Cognitive Lexicon.

- The cognitive core remains the single source of reasoning: every decision
  the product exposes must originate from the canonical flow.
- External capabilities are labeled as such in code and docs (precedent:
  D-2026-08-07 for SAP).
- The product blueprint defines the boundaries: MVP scope, data schema,
  API surface, and integration contracts. Changes to the blueprint follow the
  same rule as the canon: recorded before the code changes.

**Consequences:**

- E2 holds: product components do not claim cognitive concept slots.
- R9 holds: the architecture guides the product code.
- The product blueprint lives in `company-os-monitor` (`docs/`) and is
  versioned with the code.
- Memory remains planned: the product must not implement it as operational.
- The first implementation of this decision is the MVP phase of the product
  blueprint in `company-os-monitor`.

> Addendum (2026-08-09) — merge del master plan: the document
> `INFRADOCTOR_MASTER_PLAN.md` (a datacenter observability roadmap) was merged
> as a **roadmap specification** into the product blueprint
> (`docs/INFRADOCTOR_MASTER_PLAN.md` in `company-os-monitor`). Per ADR-0002 and
> this decision, its phases map to canonical concepts or are labeled external;
> the alternative brands ("InfraDoctor"/"DOGO") are discarded. The predictive
> engine ported from the plan (`product/services/predictor.py`) produces
> expected patterns that feed the canonical flow as Q3 evidence; it never
> decides on its own. Every forecast is labeled "not calibrated" until a
> measured ECE exists (Mode Local). The parallel prototype (`doctor/`) is
> retired; its valuable capabilities were re-routed through the canonical flow.

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

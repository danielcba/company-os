# Architecture Decision Record 0003

Title: Adopt Monitor Memory & Learning Layer as Framework Memory Capability

Status: Accepted

Date: 2026-08-30

Supersedes: ADR-0002 (regarding "Memory remains planned" restriction)

Related: ADR-0001, ADR-0002, P7

---

## Context

Company OS is the cognitive center of an organization (ADR-0001). Its first
implementation, `company-os-monitor`, has matured beyond the canonical one-shot
pipeline into a system that learns from outcomes.

The Monitor now implements a complete Memory & Learning layer:

- **Memory Consolidation**: compares expected vs actual outcomes for committed
  Decisions, computing calibration feedback (bounded [-1,1]), Brier score, and
  ECE. Classifies outcomes as corroborated, contradicted, or inconclusive.
- **Learning Loop**: orchestrates the full P7 cycle for a Decision:
  Consolidation → Pattern Refinement → Context Revision → Insight Transformation
  → trace to affected artifacts → persist signals to Memory Ledger.
- **Memory Ledger**: append-only ledger persisting learning signals, idempotent
  by content-addressed hash, tenant-scoped.
- **Pattern Refinement**: attributes Decision outcomes to Patterns via
  traceability chains, recommends keep/degrade/deactivate.
- **Context Revision**: attributes Decision outcomes to Contexts, recommends
  keep/review/consider_competitor. Never auto-activates a Context (P2).
- **Insight Transformation**: journals the transformation of each Insight,
  classifying as revised/stable/unchanged. Descriptive only (P4).
- **Hypothesis Evaluation**: evaluates candidate Hypotheses against Evidence
  using formal rules. FALSIFIED if falsification criterion met; CONFIRMED if
  predictions corroborated above threshold; INSUFFICIENT otherwise.
- **Confidence Calibration**: computes S (evidential support), C (explanatory
  coherence), ECE (historical calibration), and C_final. Already Official.
- **Cognitive Trace**: read model reconstructing provenance chains from
  canonical stores. Not a new cognitive stage.
- **Cognitive Timeline**: read model reconstructing chronological sequences of
  cognitive events. Read-only, never fabricates (P1).

The Framework currently labels Memory as "planned" or "future" throughout its
documentation. ADR-0002 states: "Memory remains planned: the product must not
implement it as operational." This was accurate when written (2026-08-09) but
no longer reflects the verified state of the Monitor. ADR-0002 is a historical
decision record and is not modified by this ADR; the evolution is expressed
here.

The Framework needs to recognize formally that Memory is implemented and
operational, without confusing architectural invariants with implementation
details.

---

## Decision

**The Framework formally adopts the Monitor's Memory & Learning layer as its
Memory capability, preserving all architectural invariants.**

### Scope

1. **Memory is no longer "planned."** It is a recognized architectural
   capability with a formal definition.
2. **P7 (Learning Through Outcome)** is realized by the Learning Loop. The
   principle remains architectural; the Loop is its concrete execution.
3. **Architectural invariants are preserved** — the Framework specifies what
   Memory does, not how it is implemented.
4. **The Monitor's implementation is the reference**, but Framework
   documentation does not encode implementation specifics.

### Invariants Preserved

- **Append-only**: Memory writes are never updated or deleted (P1).
- **Tenant-scoped**: All Memory operations are scoped to a tenant.
- **Idempotency**: Duplicate signals are deduplicated by content hash.
- **Provenance**: Every Memory signal traces back to a Decision and Outcome.
- **Cognitive Boundary**: Memory does not imply action authority.
- **Evidence Boundary**: Reasoning operates on Evidence, never on raw
  Observations.
- **No fabrication**: Memory read models reconstruct from canonical stores,
  never invent data.

### What Changes in the Framework

- Memory Layer status: `planned` → `operational`.
- Learning Loop: documented as the realization of P7.
- Memory Ledger: defined as the persistence mechanism.
- Evaluation: formalized as a capability with lifecycle.
- Pattern Refinement, Context Revision, Insight Transformation: documented as
  Learning sub-capabilities.
- Cognitive Trace and Timeline: documented as architectural read models.

### What Does NOT Change

- ADR-0001 (Company OS is the Brain): unaffected.
- ADR-0002 (COS-Monitor is the Product): preserved as historical record. The
  "Memory remains planned" restriction was accurate at time of acceptance.
  This ADR supersedes that specific restriction by introducing a new decision.
- The 10 Core Concepts and their definitions: unchanged (Memory is added as
  concept #11, not a modification of existing concepts).
- The 7 Cognitive Principles: unchanged.
- The Design Rules (R1-R7): unchanged.
- The Cognitive Boundary: unchanged.
- The Perception → Reasoning → Confidence → Action pipeline: unchanged.

---

## Consequences

### Positive

- The Framework accurately reflects the verified state of the system.
- P7 gains a concrete realization (Learning Loop) without losing its
  architectural status.
- Memory capabilities are documented at the Framework level, preventing
  drift between architecture and implementation.
- Future implementations can reference the Framework's Memory specification
  without depending on Monitor-specific code.

### Negative

- ADR-0002 contains a "Memory remains planned" restriction that is now
  superseded by this ADR. ADR-0002 itself is not modified (historical record).
- The Framework now carries a larger surface area for Memory documentation.
- The distinction between architectural specification and implementation
  reference must be carefully maintained.

---

## Compliance

This ADR authorizes the documentation of Memory & Learning capabilities at the
Framework level. It does not authorize:

- Modifying Monitor code beyond documentation alignment.
- Adding implementation-specific requirements to the Framework.
- Creating new architectural layers or principles.
- Duplicating Monitor logic in the Framework.

The architecture guides the code, never the opposite (R7). The Monitor's
implementation is evidence that the architecture works, not the source of
architectural truth.

# Engineering

Version: 1.0
Status: Official
Owner: Company OS

---

## Purpose

Define the engineering discipline of Company OS.

Company OS is not only a cognitive architecture.
It is a way of engineering cognition.

The discipline ensures that the architecture remains coherent, recoverable, and independent of any single conversation or implementation.

---

## Core Conviction

> The architecture should guide the code, never the opposite.

Engineering serves the architecture.
The architecture is never bent to convenience.

---

## Engineering Principles

### E1 — Design the Thinking First

The cognitive architecture is defined and validated before implementation.

Every software component implements a cognitive contract that already exists in the lexicon.

### E2 — Concepts Are Contracts

Every concept is a Cognitive Contract: Input → Transformation → Output.

Implementation is the computational expression of that contract.

A component that does not map to a concept has no place in the system.

### E3 — The Repository Is the Single Source of Truth

The repository holds the canonical state of the project.

Discovery happens in conversations.
Canonicalization happens in the repository.

Every stable discovery ends in GitHub.

### E4 — State Recovery Is a First-Class Concern

The project must be able to continue independently of any conversation.

The `state/` directory records the current state.

The repository must always tell the same story as the journey that produced it.

### E5 — Decisions Are Documented

Every architectural decision is recorded in `decisions/`.

Major decisions are documented as ADRs.

Proposed changes pass through the RFC process.

### E6 — Journaling Is Required

The `journal/` records discoveries, transformations, and decisions.

A journal entry is required at every point where the canonical state changes — each session that creates, modifies, or deletes a repository file must leave one entry, not by calendar.

The operational rule is [Directive 002](../../decisions/decisions.md#directive-002--journaling-at-the-point-of-change).

The journal preserves the sequence of discoveries, not only their results.

A project without a journal cannot be recovered.

---

## Engineering Workflow

1. **Discover** — insights emerge through research and reasoning.
2. **Define** — every stable insight is captured as a document following a template.
3. **Validate** — each definition is evaluated against the Cognitive Principles and Design Rules.
4. **Canonicalize** — validated definitions become Official in the repository.
5. **Recover** — `state/project-state.md` is updated so the next session can continue.

---

## Verification

Every Official document must satisfy:

- **Consistency** — no contradiction with the Principles, Ontology, or Relationships.
- **Traceability** — every claim links to its source.
- **Completeness** — every concept implements a full Cognitive Contract.
- **Stability** — definitions are stable; only mechanisms evolve.

---

## Implementation Discipline

When implementation begins:

- One component per cognitive capability.
- One contract per component.
- No component bypasses the cognitive boundary.
- Every conclusion carries confidence.
- Every decision is recorded.

---

## Evolution Notes

Future versions may define:

- Component specifications derived from Cognitive Contracts
- Verification and test protocols
- CI/CD aligned with the engineering workflow
- Tooling for ontology consistency checks

---

> First understand.
> Then distill.
> Only then continue.

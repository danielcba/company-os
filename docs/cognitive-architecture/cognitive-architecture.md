# Cognitive Architecture

Version: 2.0
Status: Official
Owner: Company OS

---

## Purpose

Define how the Cognitive Lexicon becomes a computational architecture.

The Lexicon defines what exists.
The Architecture defines how it runs.

This document is the bridge between the ontology and the engineering.

---

## Architectural Position

Company OS is the cognitive center of an organization ([ADR-0001](../../adr/ADR-0001-company-os-is-the-brain.md)).

The architecture must therefore separate the cognitive layers so that no component can violate a Cognitive Principle.

The reference architecture follows the structure of the Common Model of Cognition: perception, working memory, declarative memory, procedural memory, action, and learning — with metacognition as a cross-cutting concern rather than a distinct component.

---

## The Cognitive Pipeline

The canonical processing cycle:

```
Reality
  ↓
Perception Layer      Observation → Evidence → Context
  ↓
Reasoning Layer       Pattern → Anomaly → Hypothesis → Insight
  ↓
Confidence            cross-cutting calibration (Learning, metacognition)
  ↓
Action Layer          Recommendation → Decision
  ↓
Memory Layer          Consolidation → Learning
  ↓
(repeats)
```

Confidence belongs to the Learning family. It is not a distinct stage: metacognition is a cross-cutting orientation that calibrates every judgment in Reasoning and Action.

Each layer implements the Cognitive Contract of its concepts: Input → Transformation → Output.

---

## Layer Responsibilities

### Perception Layer

- Captures Observations immutably.
- Organizes Observations into Evidence.
- Activates mental models and selects the Active Context by explanatory coherence.

Constraint: perception does not interpret. It only captures, organizes, and selects the most coherent interpretation.

### Reasoning Layer

- Detects Patterns.
- Identifies Anomalies.
- Generates and evaluates Hypotheses.
- Restructures understanding into Insights.

Constraint: reasoning acts on knowledge, never directly on the world.

### Confidence and Metacognition (Learning, cross-cutting)

- Computes calibrated Confidence for every judgment.
- Monitors the quality of reasoning.
- Detects impasse and calibration failure.
- Triggers restructuring when the current frame fails.

Confidence is a Learning-family capability. Metacognition is a cross-cutting orientation, not a separate family or a distinct layer. Constraint: it is not a separate oracle. It reasons over explicit representations of the system's own cognitive state.

### Action Layer

- Produces Recommendations with rationale, alternatives, and confidence.
- Commits Decisions with traceability and expected outcomes.

Constraint: the action layer is the only path from intent to execution. Perception and reasoning never execute actions directly.

### Memory Layer (operational)

- Consolidates Decisions and Outcomes through the Learning Loop.
- Supports Confidence with historical calibration via outcome pairs.
- Enables Learning through comparison of expected and actual outcomes.
- Persists learning signals in an append-only Memory Ledger.

The Memory Layer realizes P7 (Learning Through Outcome). Its concrete
realization is the Learning Loop: Decision → Outcome → Consolidation →
Learning Signal → Memory → Pattern Refinement → Context Revision →
Insight Transformation.

Constraint: memory is stratified by function (working, episodic, semantic,
procedural). All Memory operations are append-only, tenant-scoped, idempotent,
and traceable to their originating Decision and Outcome.

---

## The Cognitive Boundary

A fundamental safety invariant:

**Perception never implies action authority.**

Raw input cannot trigger action without passing through reasoning, confidence, and the action layer.

This mirrors the architecture of biological cognition, where sensory processing and motor output are separated by the central executive. In Company OS, this design is intended to mitigate the failure modes of purely reactive systems — including prompt injection and authorization bypass. This is a stated design intent to be tested empirically, not a proven guarantee.

The pipeline is:

```
Perception → Reasoning → Confidence → Action
```

No shortcut is allowed.

---

## Confidence as a First-Class Output

Every conclusion that influences action carries:

1. A confidence score,
2. The justification of that score,
3. A calibration estimate.

Confidence is computed from:

- Evidential support,
- Explanatory coherence,
- Historical performance of similar judgments.

---

## Memory Stratification

| Memory | Function | Analogy |
|---|---|---|
| Working | Active reasoning state | Context window |
| Episodic | What happened, when, in what order | Session and outcome logs |
| Semantic | Facts and relationships | Knowledge base |
| Procedural | How to do things | Cognitive contracts and policies |

---

## Learning Loop

Every Decision produces an outcome.

The Learning Loop is the concrete realization of P7 (Learning Through Outcome).
It is not a phase — it is a continuous cycle that runs after each Decision
produces an observable Outcome.

### Sequence

```
Decision
  → Outcome (expected vs actual)
  → Consolidation (compute calibration feedback, Brier score, ECE)
  → Learning Signal (identity, provenance, target)
  → Memory (append-only ledger)
  → Pattern Refinement (keep / degrade / deactivate)
  → Context Revision (keep / review / consider_competitor)
  → Insight Transformation (revised / stable / unchanged)
```

### Invariants

- Every Memory signal traces to a Decision and its Outcome.
- All writes are append-only (P1), tenant-scoped, idempotent.
- No component may auto-modify its own architecture based on Learning signals.
  Learning produces signals; modification is a separate human-deliberated
  action.
- Reasoning operates on Evidence, never on raw Observations.
- Context never auto-activates without validation (P2).
- Insight Transformation is descriptive only: it journals what changed, not
  what should change (P4).

### What the System Can Learn

- Which Patterns are reliable (contradiction ratio from outcomes).
- Which Contexts are explanatory (outcome attribution).
- How well Confidence is calibrated (historical Brier/ECE).
- Which Insights have been revised by new outcomes.

### What the System Cannot Learn Automatically

- New Observations or Evidence (perception is separate).
- New Decisions (action is separate).
- Architectural changes (architecture guides code, R7).
- Causal mechanisms (correlation is not causation).

### Sub-capabilities

| Sub-capability | Purpose | Relationship |
|---|---|---|
| Consolidation | Compute calibration feedback from outcomes | Feeds Confidence calibration |
| Pattern Refinement | Attribute outcomes to Patterns | Recommends keep/degrade/deactivate |
| Context Revision | Attribute outcomes to Contexts | Recommends keep/review/consider_competitor |
| Insight Transformation | Journal Insight changes from outcomes | Classifies revised/stable/unchanged |
| Memory Ledger | Persist learning signals | Append-only, idempotent, tenant-scoped |

---

## Evaluation

Evaluation is the Learning sub-capability that manages the Hypothesis lifecycle.

### Purpose

Hypotheses are generated by Reasoning but must be formally evaluated against new
Evidence before they can influence action. Evaluation provides the structured
process for this assessment.

### Lifecycle

```
candidate
  ↓ (enough predictions corroborated, Confidence above threshold, no falsification)
confirmed
  ↓ (falsification criterion met by Evidence)
falsified
  ↓ (insufficient evidence to decide)
insufficient → remains candidate
```

- **candidate**: Initial state. A Hypothesis awaiting evaluation against Evidence.
- **confirmed**: Sufficient predictions corroborated AND Confidence above
  threshold AND no falsification criterion met.
- **falsified**: At least one falsification criterion met by Evidence. This is
  terminal — Confidence cannot override falsification.
- **insufficient**: Not enough evidence to confirm or falsify. The Hypothesis
  remains a candidate for future evaluation.

### Invariants

- **Reasoning operates on Evidence, not raw Observations.** Evaluation is
  evidence-based. The Evidence Boundary is enforced: no Hypothesis may be
  evaluated against raw Observations.
- **Falsification is terminal.** Once a Hypothesis is falsified, it cannot be
 复活 by Confidence or any other mechanism. This is a safety invariant.
- **Confidence gating.** Confirmation requires a minimum Confidence threshold.
  This prevents premature confirmation of weakly supported Hypotheses.
- **Append-only evaluations.** Each evaluation is a new record. No evaluation
  is updated or deleted. Provenance is preserved.
- **Tenant-scoped.** All evaluations are scoped to a tenant.

### Relationship with Evidence

- Evidence is the input to Evaluation.
- New Evidence may corroborate or contradict Hypothesis predictions.
- The Evidence Boundary (reasoning operates on Evidence, never on raw
  Observations) is architecturally enforced.

### Relationship with Confidence

- Confidence gates confirmation: a Hypothesis requires minimum Confidence to
  be confirmed.
- Confidence cannot override falsification.
- Confidence is itself evaluated through the Learning Loop (historical
  calibration via Brier score and ECE).

### Provenance

Every evaluation traces to:
- The Hypothesis being evaluated.
- The Evidence used for evaluation.
- The Confidence score at time of evaluation.
- The resulting lifecycle state.

---

## Pattern Refinement

Pattern Refinement is a Learning sub-capability that attributes Decision
outcomes to Patterns.

### Purpose

After a Decision produces an Outcome, Pattern Refinement traces back through
the cognitive chain (Decision → Recommendation → Hypothesis → Pattern) to
attribute the outcome to the Patterns that informed the Decision.

### Signals

- **keep**: The Pattern has sufficient corroborating outcomes. No action needed.
- **degrade**: The Pattern has a rising contradiction ratio. Should be reviewed.
- **deactivate**: The Pattern has a high contradiction ratio (above threshold).
  Should be deactivated.

### Invariants

- Minimum samples required before refinement (premature refinement is
  unreliable).
- Contradiction ratio is computed from attributed outcomes, not from
  Confidence scores.
- Refinement is descriptive (recommends), not prescriptive (does not
  auto-modify).

---

## Context Revision

Context Revision is a Learning sub-capability that attributes Decision
outcomes to Contexts.

### Purpose

After a Decision produces an Outcome, Context Revision traces back through
the cognitive chain (Decision → Recommendation → Hypothesis → Pattern → Context)
to attribute the outcome to the Contexts that were active.

### Signals

- **keep**: The Context has sufficient corroborating outcomes.
- **review**: The Context has a rising contradiction ratio. Should be reviewed.
- **consider_competitor**: A competing Context may be more explanatory.

### Invariants

- Minimum samples required before revision.
- Context Revision never auto-activates a Context. Activation follows P2
  (Explanatory Coherence): Context activates by coherence competition, not
  by Learning signal alone.
- Revision is descriptive (recommends), not prescriptive (does not
  auto-modify).

---

## Insight Transformation

Insight Transformation is a Learning sub-capability that journals the
transformation of each Insight.

### Purpose

When a Decision produces an Outcome that affects an Insight, Insight
Transformation records the prior understanding and the mental model update.

### Classification

- **revised**: The Insight's understanding has changed based on the Outcome.
- **stable**: The Insight's understanding remains consistent.
- **unchanged**: No Outcome attribution available for this Insight.

### Invariants

- Transformation is descriptive only (P4): it records what changed, not
  what should change.
- No auto-modification of the cognitive model. Insight Transformation
  produces a journal entry, not an instruction.
- Provenance traces to the originating Decision and Outcome.

---

## Memory Ledger

The Memory Ledger is the persistence mechanism for Learning signals.

### Purpose

Persist every learning signal from Consolidation, Pattern Refinement, Context
Revision, and Insight Transformation in a durable, append-only store.

### Properties

- **Append-only**: Records are never updated or deleted (P1).
- **Tenant-scoped**: All records are scoped to a tenant.
- **Idempotent**: Duplicate signals are deduplicated by content hash.
- **Traceable**: Every record traces to its originating signal type,
  target, Decision, and Outcome.

### Signal Identity

Each signal has a deterministic identity derived from its content:
signal type + target type + target id + content hash. This enables
idempotent writes without requiring external UUID generation.

### Replay and Deduplication

- The Ledger can be replayed to reconstruct Learning state.
- Deduplication occurs at write time via the content hash. Duplicate
  signals are silently ignored (ON CONFLICT DO NOTHING).

---

## Cognitive Trace

Cognitive Trace is an architectural read model.

### Purpose

Given a Report (root entity), reconstruct the full provenance chain:
Report → Decision → Recommendation → Confidence → Hypothesis → Anomaly → Pattern → Context → Evidence → Observation.

### Properties

- **Read-only**: Reconstructs from canonical stores, never fabricates data.
- **Tenant-scoped**: All queries are scoped to a tenant.
- **Partial on broken provenance**: If the provenance chain is incomplete,
  the trace is marked `partial` with `warnings`. It is never fabricated.

### Architectural Status

Cognitive Trace is NOT a new cognitive stage or a new source of truth.
It is a read model that reconstructs existing data for observability
and debugging purposes.

---

## Cognitive Timeline

Cognitive Timeline is an architectural read model.

### Purpose

Reconstruct the chronological sequence of cognitive events for a tenant
from all canonical stores: Observation, Evidence, Context, Pattern, Anomaly,
Hypothesis, Insight, Recommendation, Decision, Report, Confidence, Audit Log.

### Properties

- **Read-only / compute-only**: Never persists new data.
- **Ordered by time**: Events are ordered chronologically.
- **Aggregated**: Combines events from 12+ canonical sources.
- **Tenant-scoped**: All queries are scoped to a tenant.

### Architectural Status

Cognitive Timeline is NOT a new source of truth. It is a read/compute
model for observability, debugging, and temporal analysis of the
cognitive pipeline.

---

## Design Rules for the Architecture

- **R1.** Every component implements exactly one cognitive capability.
- **R2.** Every component has a defined Cognitive Contract.
- **R3.** The cognitive boundary is enforced architecturally.
- **R4.** No conclusion influences action without confidence.
- **R5.** Every decision is recorded with rationale and expected outcomes.
- **R6.** Explanations are first-class outputs at every layer.
- **R7.** The architecture guides the code, never the opposite.

---

## Evolution Notes

Future versions may define:

- Mental model representation and activation
- Coherence evaluation algorithms
- Hypothesis generation mechanisms
- Calibration protocols and tooling

---

> The architecture is beginning to reveal itself instead of being invented.

# Cognitive Architecture

Version: 1.0
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
Memory Layer          Consolidation → Learning (planned)
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

### Memory Layer (planned)

- Consolidates Observations, Decisions, and Outcomes.
- Supports Confidence with historical calibration.
- Enables Learning through comparison of expected and actual outcomes.

Constraint: memory is stratified by function (working, episodic, semantic, procedural).

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

The comparison of expected and actual outcomes:

- Updates Confidence calibration,
- Refines Patterns,
- Revises Context,
- Consolidates Memory.

Learning is not a phase. It is a continuous loop.

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
- Calibration measurement and reporting
- The Memory subsystem in full

---

> The architecture is beginning to reveal itself instead of being invented.

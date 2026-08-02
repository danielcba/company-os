# Pattern

Version: 1.0
Status: Official
Owner: Company OS
Cognitive Family: Reasoning
Capability: Generalize

---

## Definition

A Pattern is a recurring structure, relation, or regularity detected within an Active Context.

Patterns reveal regularity.
Laws explain regularity.

Company OS does not invent patterns.
It detects regularities that are present in the available context and that satisfy a sufficient degree of support.

---

## Purpose

The purpose of Pattern is to compress the variability of experience into regularities that can support prediction and explanation.

Patterns convert the continuous stream of Context into discrete, recognizable, and reusable structures.

Without patterns, every situation would be new, and no learning or prediction would be possible.

---

## Why It Matters

Reasoning requires generalization.

A system that only accumulates Context without detecting Patterns can describe the past but cannot anticipate the future.

Patterns are the bridge between what has been observed and what can be expected.

The principle defines what is possible.
The context defines the conditions.
The pattern is the solution that emerges under those conditions.

---

## Cognitive Contract

### Input

- Active Context
- A library of known patterns (or an open search space)

### Transformation

Detect recurrent structures, correlations, or sequences within the Active Context, and compare them against known patterns.

### Output

- Candidate Pattern(s)
- A measure of pattern strength (support, frequency, or statistical significance)

---

## Relationships

### Produced By

Context

### Depends On

Context

### Supports

Hypothesis

### Leads To

Anomaly (when a deviation from an expected pattern is detected)

### Refines

Context (a confirmed pattern refines the interpretation of new evidence)

---

## Examples

### Example 1 — Infrastructure

Active Context: Over four weeks, the ERP backup fails every Friday at 23:00.

Pattern: "Backup failures recur with a weekly periodicity, always on Friday."

This pattern supports the hypothesis that a scheduled job conflicts with the backup window.

### Example 2 — Access

Active Context: Login failures cluster in five-minute bursts every night.

Pattern: "Authentication failures occur in short temporal bursts at regular intervals."

This pattern is consistent with coordinated authentication activity, but it does not yet claim intent.

---

## Non-Examples

"Friday night backups always fail because of the maintenance job."

This is an explanation, not a Pattern.

A Pattern describes regular structure.
A Hypothesis proposes its cause.

"The server will fail next month."

This is a prediction, not a Pattern.

---

## Design Implications

Company OS must separate the detection of a Pattern from the explanation of it.

Pattern detection is a generalization step.
Explanation belongs to Context and Hypothesis.

Patterns are probabilistic and revisable.
A pattern is a working regularity, not a law.

The strength of a pattern should be quantified so that later cognitive steps (Hypothesis, Confidence, Recommendation) can weigh it appropriately.

---

## Evolution Notes

Future versions may define:

- Statistical pattern detection methods
- Sequential and temporal pattern classes
- Hierarchical patterns (patterns composed of patterns)
- Pattern decay and obsolescence

The distinction between Pattern and Law should remain stable.

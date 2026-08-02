# Relationships

Version: 1.1
Status: Official
Owner: Company OS

---

## Purpose

Relationships define how cognitive concepts interact.

Concepts describe knowledge.
Relationships enable reasoning.

Every relationship in Company OS is:

- **Typed** — one of the ten formal relationship types,
- **Directed** — it has a source and a target,
- **Meaningful** — it states what the source does to the target,
- **Traceable** — every instance of a relationship is justified by the concepts it connects.

The type set is closed: no relationship exists in the Lexicon that is not one of the ten types below.

---

## Relationship Types

### Produces

One concept generates another.

Notation: `A → B`

The source is the origin of the target.

Examples:

- Observation → Evidence
- Evidence → Context

---

### Requires

A concept cannot exist without another.

Notation: `A ⇠ B`

B cannot function unless A is present.

Examples:

- Context ⇠ Evidence
- Hypothesis ⇠ Pattern
- Decision ⇠ Recommendation

---

### Supports

One concept increases confidence in another.

Notation: `A ⇒ B`

The source provides evidential weight to the target.

Examples:

- Pattern ⇒ Hypothesis
- Evidence ⇒ Hypothesis

---

### Leads To

One concept naturally progresses into another.

Notation: `A ⟹ B`

The source, once active, drives the system toward the target.

Examples:

- Insight ⟹ Recommendation
- Recommendation ⟹ Decision
- Decision ⟹ Memory (planned)

---

### Contradicts

One concept invalidates or weakens another.

Notation: `A ⊣ B`

The source is incompatible with the target, reducing its coherence.

Examples:

- Evidence ⊣ Hypothesis (new evidence can eliminate a hypothesis)
- Anomaly ⊣ Context (a deviation weakens the active interpretation)

---

### Refines

New material adjusts an existing structure.

Notation: `A ▸ B`

The source modifies, sharpens, or corrects the target without replacing it.

Examples:

- Observation ▸ Context
- Anomaly ▸ Pattern

---

### Enables

One concept makes another operationally possible without being its origin.

Notation: `A ⇢ B`

The source creates the condition under which the target can exist or act.

Examples:

- Evidence ⇢ Context

---

### Applies To

One concept is applied to, or assesses, another.

Notation: `A ↦ B`

The source evaluates, governs, or targets the object.

Inverse form: Evaluated By.

Examples:

- Confidence ↦ Hypothesis, Recommendation, Decision

---

### Affects

One concept modulates the strength, threshold, or behavior of another without replacing it.

Notation: `A ⇝ B`

Examples:

- Confidence ⇝ Recommendation strength
- Confidence ⇝ Decision threshold

---

### Improved By

One concept improves through feedback returned by another.

Notation: `A ← B`

Examples:

- Confidence ← Memory (planned)
- Confidence ← Learning

---

## Passive Inverse Forms

Concept files use the following passive forms, each equivalent to the inverse of a formal type:

- Produced By — inverse of Produces
- Depends On — inverse of Requires
- Supported By — inverse of Supports
- Evaluated By — inverse of Applies To

---

## Relationship Table

| From | Relationship | To |
|---|---|---|
| Observation | Produces | Evidence |
| Observation | Refines | Context |
| Evidence | Requires | Observation |
| Evidence | Supports | Hypothesis |
| Evidence | Enables | Context |
| Context | Produces | Pattern |
| Context | Requires | Evidence |
| Pattern | Supports | Hypothesis |
| Pattern | Leads To | Anomaly |
| Anomaly | Contradicts | Context |
| Anomaly | Leads To | Hypothesis |
| Anomaly | Refines | Pattern |
| Hypothesis | Contradicts | Hypothesis |
| Hypothesis | Leads To | Insight |
| Hypothesis | Leads To | Recommendation |
| Insight | Refines | Context |
| Insight | Refines | Hypothesis |
| Insight | Leads To | Recommendation |
| Confidence | Applies To | Hypothesis, Recommendation, Decision |
| Confidence | Affects | Recommendation strength, Decision threshold |
| Confidence | Improved By | Memory (planned), Learning |
| Recommendation | Leads To | Decision |
| Recommendation | Requires | Confidence |
| Decision | Leads To | Memory (planned) |
| Memory (planned) | Supports | Confidence |

---

## Cognitive Flow as a Relationship Chain

```
Reality → Observation → Evidence → Context → Pattern → Anomaly
       → Hypothesis → Insight → Confidence → Recommendation → Decision → Memory (planned)
```

---

## Design Rules for Relationships

- No relationship exists without a defined type.
- No relationship contradicts the direction of the Cognitive Flow without justification.
- Relationships are evaluated by the coherence they create or destroy.
- The relationship map is the same for every agent, human or artificial.

---

## Evolution Notes

Future versions may define:

- Weighted relationships
- Temporal relationships
- Non-binary relationships
- Relationship discovery (patterns in the relationship map itself)

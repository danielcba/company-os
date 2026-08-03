# Recommendation

Version: 1.0
Status: Official
Owner: Company OS
Cognitive Family: Action
Capability: Propose

---

## Definition

A Recommendation is a proposed course of action derived from the current understanding and its associated confidence.

A recommendation is an offer.
A decision is a commitment.

---

## Purpose

The purpose of Recommendation is to translate understanding into an actionable option.

Recommendations bridge the gap between what the system believes and what the system (or its human counterpart) can do.

---

## Why It Matters

Understanding that cannot be translated into action has limited value.

Recommendations structure action as an explicit, comparable, and auditable option, accompanied by its expected consequences and its confidence.

A good recommendation must state:

1. What to do,
2. Why,
3. What is expected to happen,
4. How confident the system is,
5. What alternative options were considered.

---

## Cognitive Contract

### Input

- Active Context
- The leading Hypothesis or Insight
- Confidence in that understanding
- The available action space

### Transformation

Derive the course of action that best serves the current purpose under the constraints of the current context.

### Output

- A Recommendation
- Its rationale
- Its expected consequences
- Its confidence
- The alternatives considered

---

## Relationships

### Depends On

Context, Hypothesis, and Confidence

### Leads To

Decision

### Evaluated By

Confidence

---

## Examples

### Example 1

Understanding: "The backup disk will reach capacity in 12 days."

Confidence: High (based on historical calibration).

Recommendation: "Expand the backup volume before day 10, or move the backup target to the new storage array."

Alternatives: "Compress older backups" and "Reduce retention window" were evaluated and considered higher risk.

### Example 2

Understanding: "Login bursts are consistent with a compromised account."

Confidence: Medium.

Recommendation: "Reset the affected account credentials and enable conditional access monitoring for 7 days before declaring the hypothesis confirmed."

---

## Non-Examples

"Run the backup now."

This is an instruction or an order, not a Recommendation.

A Recommendation carries rationale, alternatives, and confidence.

"Decision: expand the disk."

This is a Decision, the consequence of accepting a Recommendation.

---

## Design Implications

Company OS must separate Recommendation from Decision.

A recommendation is advisory and reversible.
A decision is committed and accountable.

Recommendations must always be traceable to the evidence, hypotheses, and confidence that produced them.

The action space must be explicit so that the system knows what it is choosing among.

---

## Evolution Notes

Future versions may define:

- Recommendation scoring and ranking
- Multi-objective action evaluation
- Recommendation under uncertainty
- The Recommendation–Decision boundary

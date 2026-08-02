# Decision

Version: 1.0
Status: Official
Owner: Company OS
Cognitive Family: Action
Capability: Commit

---

## Definition

A Decision is a commitment to a course of action, selected from available alternatives, based on the current understanding and its confidence.

A decision ends deliberation.
It does not end learning.

---

## Purpose

The purpose of Decision is to convert understanding into committed action and to create the conditions for accountability.

Without decisions, cognition produces only analysis.

---

## Why It Matters

Every meaningful effect of Company OS on the world passes through decisions.

A decision:

1. Selects one course of action,
2. Binds resources or authority,
3. Becomes observable,
4. Produces outcomes that can be compared against expectations.

Decisions are the points where cognition meets the world, and where the quality of the entire cognitive pipeline is finally tested.

---

## Cognitive Contract

### Input

- One or more Recommendations
- Their confidence scores
- Purpose and constraints
- Risk tolerance

### Transformation

Select the course of action that best balances expected value and risk, and commit to it.

### Output

- A Decision
- Its recorded rationale
- Its expected outcomes, stated as falsifiable predictions in observable terms
- The confidence score associated with the decision
- The commitment authority under which it was taken

---

## Falsifiability

A Decision is a falsifiable prediction.

Its expected outcomes must be stated in observable, verifiable terms before the decision is executed.

A decision is scientifically meaningful only if it can be shown wrong by observation (Popper, 1934):

- If the observed outcome matches the expected outcome, the decision and the Confidence that supported it are confirmed.
- If the observed outcome contradicts the expected outcome, the supporting Context, Hypothesis, or Confidence calibration must be revised.

The comparison of expected and actual outcomes is the primary input to the Confidence calibration model and to the Learning loop.

This rule converts every decision from an act of authority into an experiment.

---

## Relationships

### Produced By

Recommendation, evaluated through Confidence

### Depends On

Context, Hypothesis, Insight, and Confidence

### Leads To

Memory (the decision and its outcome become part of the system's history)

### Evaluated By

Outcome (through Memory and Learning)

---

## Examples

### Example 1

Recommendation: "Expand the backup volume before day 10."

Decision: "Expand the volume on day 8, increase the alert threshold to 90%, and document the change."

Expected outcome: "Backup capacity remains above 20% for the next 6 months."

### Example 2

Recommendation: "Reset credentials and monitor for 7 days."

Decision: "Reset credentials, revoke sessions, and hold a review on day 7."

Expected outcome: "Login bursts stop; if they persist, escalate to a security review."

---

## Non-Examples

"We should probably expand the disk."

This is a Recommendation, not a Decision.

A decision is a commitment with an owner, a timeline, and expected outcomes.

"Let's keep an eye on it."

This is an indefinite intention, not a Decision.

A decision selects a definite course of action.

---

## Design Implications

Company OS must record every decision with its full trace: evidence, context, hypotheses, confidence, alternatives, and expected outcomes.

Decisions must be reversible when the underlying evidence changes.

The decision layer must respect a cognitive boundary: perception and reasoning inform decisions, but they do not execute them autonomously unless explicitly authorized.

The comparison between expected and actual outcomes is the primary learning signal of the entire system.

---

## Evolution Notes

Future versions may define:

- Decision under uncertainty (decision theory)
- Risk and expected value models
- Decision authority and accountability
- The Decision–Memory–Learning loop

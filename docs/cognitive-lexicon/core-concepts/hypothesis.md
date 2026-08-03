# Hypothesis

Version: 1.0
Status: Official
Owner: Company OS
Cognitive Family: Reasoning
Capability: Predict

---

## Definition

A Hypothesis is a testable explanation of an observed or anomalous situation, proposed to account for available Evidence, Patterns, or Anomalies.

A hypothesis is a commitment to an explanation, held tentatively until evidence decides.

---

## Purpose

The purpose of Hypothesis is to make the world predictable again.

When a Pattern is confirmed or an Anomaly appears, the system needs an explanation that:

1. Accounts for the existing evidence,
2. Generates testable predictions,
3. Can be compared against competing explanations.

---

## Why It Matters

Reality does not explain itself.

Intelligence must generate plausible explanations and then evaluate them.

Hypotheses transform surprise into inquiry.

In the language of explanatory coherence, a hypothesis is accepted when it coheres better than its competitors with the full body of evidence.

---

## Cognitive Contract

### Input

- Active Context
- Patterns and/or Anomalies
- A library of mental models

### Transformation

Generate candidate explanations that account for the current situation and are consistent with the most coherent mental model.

### Output

- One or more candidate Hypotheses
- The predicted consequences of each hypothesis
- A falsification criterion for each hypothesis: the concrete observable outcome that, if it occurred, would demonstrate the hypothesis is false

---

## Relationships

### Supported By

Evidence and Pattern

### Contradicts

Competing Hypotheses

### Evaluated By

Confidence

### Leads To

Insight and Recommendation

---

## Examples

### Example 1

Anomaly: "Backup fails on Tuesday instead of Friday."

Candidate Hypotheses:

- H1: The Friday maintenance job changed its schedule.
- H2: The disk where backups are written reached capacity.
- H3: A new nightly antivirus scan interferes with the backup window.

Each hypothesis predicts different observations, which allows discrimination between them.

### Example 2

Pattern: "Authentication bursts occur nightly."

Candidate Hypotheses:

- H1: A compromised account is being probed.
- H2: A misconfigured application retries logins in a loop.
- H3: An external monitoring tool is testing credentials.

---

## Non-Examples

"The backup failed because the disk is full."

If this is asserted as established fact without testing, it is an assumption, not a Hypothesis.

A Hypothesis must be falsifiable and must predict consequences.

"The server will fail."

This is a prediction detached from explanation.

A Hypothesis pairs explanation with prediction.

---

## Design Implications

Company OS must maintain multiple competing hypotheses simultaneously.

Premature convergence on a single explanation is a cognitive failure.

Hypotheses must be represented with their evidential support and their predicted consequences, so that future observations can confirm or eliminate them.

The architecture must follow the principle of explanatory coherence: accept the hypothesis that maximizes coherence, reject those that contradict it.

---

## Evolution Notes

Future versions may define:

- Hypothesis generation mechanisms
- Abductive inference support (Peircean abduction)
- Hypothesis evaluation protocols
- The relationship between Hypothesis and Confidence

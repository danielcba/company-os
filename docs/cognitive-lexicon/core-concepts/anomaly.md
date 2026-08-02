# Anomaly

Version: 1.0
Status: Official
Owner: Company OS
Cognitive Family: Reasoning
Capability: Detect Deviation

---

## Definition

An Anomaly is a deviation from an expected Pattern that exceeds a defined tolerance threshold.

An anomaly is not an error.
It is a signal.

---

## Purpose

The purpose of Anomaly is to alert the cognitive system that reality is not behaving according to the current model.

Anomalies interrupt automatic processing and redirect attention toward the unexpected.

---

## Why It Matters

A system that only recognizes Patterns becomes dangerously stable.

It extrapolates the past and becomes blind to change.

Anomalies are the cognitive mechanism through which the system discovers that its model of the world is incomplete.

They are the first step of learning.

---

## Cognitive Contract

### Input

- Active Context
- Expected Pattern(s)
- Tolerance thresholds

### Transformation

Compare the Active Context against the expected pattern and measure the magnitude of deviation.

### Output

- An Anomaly
- A quantified deviation score
- The pattern(s) that were violated

---

## Relationships

### Contradicts

Context (an anomaly weakens the explanatory coherence of the active context)

### Leads To

Hypothesis (anomalies motivate new explanations)

### Refines

Pattern (persistent anomalies force pattern revision)

---

## Examples

### Example 1

Expected Pattern: "Backup failures occur only on Friday."

Observation: The backup fails on Tuesday.

Anomaly: A failure occurred on an unexpected day.

### Example 2

Expected Pattern: "Authentication failures occur in five-minute bursts at night."

Observation: 200 failed logins occur in 40 seconds during business hours.

Anomaly: The burst pattern changed in frequency, duration, and timing.

---

## Non-Examples

"A login failure occurred."

This is an Observation, not an Anomaly.

The anomaly exists only relative to an expected pattern.

"The network is compromised."

This is a Hypothesis, not an Anomaly.

---

## Design Implications

Anomaly detection must be defined relative to patterns, never absolutely.

Without an expected pattern, no deviation can be identified.

Tolerance thresholds must be explicit, auditable, and purpose-dependent.

Company OS must treat anomalies as priority signals that trigger the reasoning cycle, not as conclusions to be acted upon directly.

---

## Evolution Notes

Future versions may define:

- Statistical anomaly scoring
- Threshold selection and calibration
- Anomaly classes (point, contextual, collective)
- Interaction with Confidence and Metacognition

# Confidence

Version: 1.0
Status: Official
Owner: Company OS
Cognitive Family: Learning
Capability: Calibrate

---

## Definition

Confidence is a calibrated estimate of the degree to which the system's current understanding is supported by evidence, coherence, and past performance.

Confidence is not a feeling.
It is a measurement.

---

## Purpose

The purpose of Confidence is to enable the cognitive system to distinguish strong conclusions from weak ones.

Confidence determines how much weight a Hypothesis, Insight, or Recommendation can carry in the decision process.

---

## Why It Matters

An intelligence that cannot estimate its own certainty cannot prioritize, cannot delegate, and cannot learn from error.

Confidence must be calibrated: a system that reports 90% confidence should be correct approximately 90% of the time.

Calibration is the bridge between subjective certainty and objective reliability.

Poor calibration — overconfidence or underconfidence — is a structural failure of cognition, not a cosmetic issue.

---

## Cognitive Contract

### Input

- The hypothesis or recommendation under evaluation
- Its evidential support
- Its explanatory coherence
- Historical performance of similar judgments

### Transformation

Compute a calibrated confidence score that integrates support, coherence, and track record.

### Output

- A confidence score
- The justification of that score
- A calibration error estimate

---

## Calibration Model

Confidence is computed, not intuited. The model below makes the computation explicit, reproducible, and falsifiable.

### 1. Evidential Support

Let H be the judgment under evaluation and E = {e₁, …, eₙ} the available evidence, each Evidence i carrying a weight wᵢ ∈ [0, 1] derived from its Quality Class (Q1–Q4, see Evidence) and a sign eᵢ ∈ {+1, −1} (supports or contradicts H). Evidence is integrated in log-odds form:

    L = L₀ + Σᵢ wᵢ·eᵢ

where L₀ is the prior log-odds of H (default L₀ = 0, a non-committal uniform prior, unless a documented base rate is available). The support score is obtained by the logistic function:

    S(H | E) = 1 / (1 + e⁻ᴸ)

### 2. Explanatory Coherence

The coherence score C(H) ∈ [0, 1] is computed as normalized constraint satisfaction over positive constraints (H explains the evidence; hypotheses that jointly explain are coherent) and negative constraints (contradiction), following the explanatory coherence program (Thagard, 1989).

### 3. Historical Calibration

For the class of previous judgments with reported confidence pᵢ and observed outcome oᵢ ∈ {0, 1}:

- Brier score: B = (1/N) Σᵢ (pᵢ − oᵢ)²
- Expected Calibration Error (ECE), binned over M bins: ECE = Σₘ (|Bₘ| / N) · |accₘ − confₘ|

### 4. Final Confidence

    C_final = [α·S + (1 − α)·C] · (1 − ECE)

with α ∈ [0, 1] fixed a priori and documented. The calibration factor penalizes historical over- or underconfidence.

### 5. Falsifiability

The computation is fully documented and identical for every agent with identical inputs. The calibration factor is measured from outcomes only; it is never adjusted to justify a particular confidence. A confidence claim is scientific only if its calibration can be verified post hoc.

### 6. Parameters and Defaults

The model has two free parameters, both fixed a priori and published with every confidence report:

- α ∈ [0, 1]: the mixing coefficient between evidential support and coherence. Default α = 0.5. The value must be documented before use and never tuned to match a desired confidence.
- M: the number of bins for the ECE. Default M = 10. The value must be stated so that the ECE is reproducible.
- L₀: the prior log-odds of H. Default L₀ = 0 (uniform prior). A non-zero prior is permitted only when derived from a documented base rate.

---

## Relationships

### Applies To

Hypothesis, Recommendation, and Decision

### Supported By

Evidence, Pattern, and Insight

### Affects

Recommendation strength and Decision threshold

### Improved By

Memory (planned) and Learning (historical outcomes)

---

## Examples

### Example 1

Hypothesis H1 (disk full) explains the backup failure with strong evidence and a high coherence score.

Hypothesis H2 (antivirus interference) explains the failure weakly and conflicts with other evidence.

Confidence in H1 is high.
Confidence in H2 is low.

The difference is derived from evidence and coherence, not from preference.

### Example 2

The system has made 120 predictions of "disk saturation within 30 days."

114 were correct.

The historical calibration suggests this class of prediction is accurate within a well-defined margin.

---

## Non-Examples

"I think this is probably the right answer."

This is subjective certainty, not Confidence.

Confidence must be derived and auditable.

"Confidence is the probability that the hypothesis is true."

This is a naive identification.

Confidence is an estimate of reliability, which must itself be calibrated and can be wrong.

---

## Design Implications

Confidence must be computed, not intuited.

Every judgment that influences action must carry a confidence score and the reasons for it.

Company OS must monitor its own calibration continuously and adjust its confidence estimates from outcome feedback.

Confidence is the primary input to metacognitive control: when calibration fails, the system must recognize it and adapt.

---

## Evolution Notes

The Calibration Model above is the first formal specification of this concept.

Future versions may refine:

- Calibration measurement protocols and tooling
- Confidence thresholds for action
- The Confidence–Memory feedback loop
- Deriving Quality Class weights from measured calibration data

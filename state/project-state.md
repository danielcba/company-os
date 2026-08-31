# Project State

Version: 1.1
Status: Official
Owner: Company OS

---

## Purpose

This document records the canonical state of Company OS.

It exists so the project can continue independently of any conversation.

If a session resumes the project, this document is the entry point.

---

## Current Phase

**Phase 2 — Architecture.**

Phase 1 (Lexicon) is complete.
Phase 2 (Architecture) has begun.

---

## Completed

### Lexicon — Official

- [x] Ten Core Concepts: Observation, Evidence, Context, Pattern, Anomaly, Hypothesis, Insight, Confidence, Recommendation, Decision
- [x] Cognitive Principles (seven)
- [x] Cognitive Families (four plus metacognition)
- [x] Ontology
- [x] Relationships
- [x] Concept Template
- [x] Roadmap

### Governance — Official

- [x] ADR-0001: Company OS is the Brain
- [x] ADR-0002: COS-Monitor is the Product
- [x] ADR-0003: Adopt Monitor Memory & Learning Layer as Framework Memory Capability
- [x] Decisions log
- [x] RFC process
- [x] Document template

### Documentation — Official

- [x] Foundation
- [x] Cognitive Architecture
- [x] Engineering
- [x] Research

### Documentation — Draft

- [ ] Product
- [ ] Business
- [ ] Brand

### Assets

- [ ] Logo and diagrams (planned)

---

## Current State of the Cognitive Flow

```
Reality → Observation → Evidence → Context → Pattern → Anomaly
       → Hypothesis → Insight → Confidence → Recommendation → Decision → Memory
                                                                 ↓
                                                  Learning Loop (consolidation → signals)
                                                                 ↓
                                        Pattern Refinement / Context Revision / Insight Transformation
```

All 11 concepts are Official. Memory is operational (ADR-0003).

---

## Next Steps

1. Formalize mental models and coherence evaluation.
2. Define the mechanisms of the reasoning layer.
3. Translate Cognitive Contracts into computational component specifications.
4. Draft the software architecture and technology selection (Phase 3).

## Product Roadmap (implementation repo `company-os-monitor`)

The product blueprint merged the datacenter-observability roadmap
(`docs/INFRADOCTOR_MASTER_PLAN.md`). Next product milestones per that roadmap:
predictive models with measured calibration (ECE), WMI/AD/VMware/Veeam/network
agents (currently skeletons), local LLM analysis, AI executive reports,
MFA/RBAC, and audit logging. All follow the blueprint-before-code rule and
map to canonical concepts or stay labeled external (D-2026-08-09, ADR-0002).

---

## How to Resume the Project

1. Read this file.
2. Read `README_ES.md` (or `README_EN.md`) for the project overview.
3. Read `docs/cognitive-lexicon/ontology.md` for the map.
4. Read `journal/` for the recent journey.
5. Verify journal compliance ([Directive 002](../decisions/decisions.md#directive-002--journaling-at-the-point-of-change)): if the canonical state changed since the last entry, write the missing entry before continuing.
6. Continue with the next step above.

---

## State Recovery History

- 2026-07-31: Lexicon completed and declared Official. Phase 2 declared open.
- 2026-08-30: Memory & Learning Layer synchronized from Monitor (ADR-0003). Memory status: planned → operational. Cognitive Architecture v2.0. Ontology v1.2.

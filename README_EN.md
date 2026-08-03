# Company OS

Version: 1.0
Status: Official

---

## What is Company OS?

Company OS is a cognitive architecture framework: a structured, principled definition of how an organization — or an intelligent system acting on its behalf — perceives, reasons, decides, and learns.

It is not a traditional operating system.

It is the brain of a company.

Company OS defines not only what an intelligent system knows, but how it thinks.

---

## Why does it exist?

Organizations make decisions that depend on observations.

Most organizations have no formal, shared language for cognition:

- What counts as a fact?
- What counts as evidence?
- How is an interpretation chosen?
- When is confidence justified?
- How is a decision committed and learned from?

Company OS exists to answer these questions with precision, so that every human and every AI agent in an organization reasons using the same cognitive architecture.

The central conviction:

> Concepts are stable.
> Intelligence lives in the transformations between them.
> Intelligence lives in the transformations of knowledge.

---

## Principles

Seven formalized Cognitive Principles — hypotheses subject to validation — govern the cognitive universe of Company OS:

1. **P1 — The Primacy of Observation.** Meaning is never extracted directly from reality.
2. **P2 — Explanatory Coherence.** Context selects the most coherent meaning supported by evidence.
3. **P3 — Stable Concepts, Transformative Intelligence.** Intelligence lives in the transformations of knowledge.
4. **P4 — Regularity and Law.** Patterns reveal regularity. Laws explain regularity.
5. **P5 — Calibrated Confidence.** Every judgment that influences action carries a calibrated estimate of its reliability.
6. **P6 — Deliberate Action.** Recommendation precedes Decision; Decision precedes Action.
7. **P7 — Learning Through Outcome.** Expected outcomes compared with actual outcomes drive learning.

Full definitions: [docs/cognitive-lexicon/cognitive-principles.md](docs/cognitive-lexicon/cognitive-principles.md)

---

## The Cognitive Flow

```
Reality → Observation → Evidence → Context → Pattern → Anomaly
       → Hypothesis → Insight → Confidence → Recommendation → Decision → Memory (planned)
```

---

## Repository Structure

```
company-os-main/
├── adr/                          Architecture Decision Records
├── decisions/                    The decisions log
├── docs/
│   ├── brand/                    Brand guidelines
│   ├── business/                 Business model
│   ├── cognitive-architecture/   The cognitive architecture
│   ├── cognitive-lexicon/        The heart of the project
│   │   ├── core-concepts/        Individual concept definitions
│   │   ├── cognitive-principles.md
│   │   ├── cognitive-families.md
│   │   ├── ontology.md
│   │   ├── relationships.md
│   │   ├── concept-template.md
│   │   └── ROADMAP.md
│   ├── engineering/              Engineering discipline
│   ├── foundation/               Foundational principles
│   ├── product/                  Product vision
│   └── research/                 Research notes
├── journal/                      Progress and discovery records
├── rfc/                          The RFC process
├── state/                        Project state (recovery point)
└── templates/                    Document templates
```

---

## Roadmap

### Phase 1 — Lexicon (Completed)

- [x] Ten Core Concepts defined and Official
- [x] Cognitive Principles formalized
- [x] Cognitive Families formalized
- [x] Ontology, Relationships, and Templates

### Phase 2 — Architecture (In Progress)

- [ ] Translate cognitive contracts into computational components
- [ ] Define Memory and the Learning mechanisms
- [ ] Formalize mental models and coherence evaluation
- [ ] Design the perception–reasoning–action boundary

### Phase 3 — Engineering

- [ ] Select the technology stack
- [ ] Implement the cognitive runtime
- [ ] Build the confidence calibration and reporting layer

### Phase 4 — Deployment

- [ ] First organizational deployment
- [ ] Validation of the Principles against real outcomes

---

## License

Released under the [Apache License 2.0](LICENSE).

---

> The architecture should guide the code, never the opposite.

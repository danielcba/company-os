# Architecture Decision Record 0002

Title: COS-Monitor Is the Product

Status: Accepted

Date: 2026-08-09

Supersedes: —

Related: ADR-0001, D-2026-08-07, D-2026-08-09

---

## Context

Company OS is the cognitive center of an organization (ADR-0001). Its first
implementation, `company-os-monitor`, implements the canonical flow
(Reality → Decision) as a one-shot pipeline with a calibrated confidence score,
plus the SAP R/3 external capability (D-2026-08-07).

A product blueprint specifies the surrounding datacenter-observability
product: telemetry agents (Linux, Windows, VMware, network), a web dashboard,
threshold alerts, executive PDF reports, multi-tenant authentication, and local
LLM analysis through an OpenAI-compatible server (LM Studio).

The name of the product is `company-os-monitor` itself. The blueprint is a
specification, not a new brand and not a new architecture.

---

## Decision

**`company-os-monitor` expands from a cognitive implementation into the product.**

The canonical flow in `app/` is the brain of the product. Everything the
blueprint adds — agents, API, dashboard, alerts, reports, authentication, LLM
client — is an external, non-canonical product capability:

1. Every product decision originates from the canonical flow. No alert, report,
   or recommendation bypasses the cognitive core.
2. External capabilities are labeled as such in code and documentation, exactly
   as the SAP integration was (D-2026-08-07).
3. The product blueprint (`docs/` in `company-os-monitor`) defines the MVP
   scope, the data schema, the API surface, and the integration contracts. It
   is versioned with the code and recorded before the code changes.
4. The name `company-os-monitor` prevails. The blueprint introduces no
   alternative product name.
5. Memory remains planned: the product must not implement it as operational.

---

## Consequences

### Positive

- Gives the product a defined identity: one name, one brain, one source of truth.
- Keeps the cognitive architecture authoritative over the product code (R9).
- Reuses the calibrated-confidence flow for every product judgment.
- Provides a repeatable rule for adding capabilities: blueprint first, code after.

### Negative

- Imposes a governance burden: product capabilities must be designed and
  recorded before implementation.
- Requires discipline to keep external capabilities from drifting into the
  cognitive layer.
- The MVP is a large surface: agents, API, dashboard, alerts, reports, auth.

---

## Compliance

No product component may claim a cognitive concept slot (E2). No component may
bypass the canonical flow to emit alerts, reports, or recommendations (R9).
Any new capability follows the blueprint-before-code rule and, when relevant,
a canon decision.

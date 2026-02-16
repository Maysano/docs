# Core Concepts of Maysano

Maysano is an operating layer for data products. It connects business intent, governance control, and execution discipline into one coherent system. These core concepts define how the platform is structured and how teams collaborate inside it.

---

## 1. Data Product

A **Data Product** in Maysano is a governed, versioned, outcome-driven asset that delivers measurable business value. It is not just a dataset.

A data product in Maysano is defined by:

- a clear purpose and expected outcomes
- accountable ownership
- governance controls that are explicit and reusable
- lifecycle status and versioning
- measurable quality and operational signals

A data product can be produced from many technical sources (pipelines, lakehouse tables, APIs, event streams), but Maysano focuses on the product layer: the structure, accountability, and governance that makes it operationally usable and trustworthy.

---

## 2. Product Version

A **Product Version** is an immutable snapshot of a data product at a point in time.

Once a version is released (e.g., to production), it should not be modified. If changes are needed, a new version is created. This ensures that consumers, contracts, SLAs, and audits can always refer to a stable definition of what was delivered.

Versioning in Maysano supports:

- traceability of changes
- safe evolution without breaking consumers
- clean governance audits
- separation between draft work and released work

---

## 3. Lifecycle State (ODPS Aligned)

Maysano follows the lifecycle model defined in the Open Data Product Specification (ODPS).

The `status` field of a data product version MUST be one of the following:

- `announcement`
- `draft`
- `development`
- `testing`
- `acceptance`
- `production`
- `sunset`
- `retired`

Each status represents a distinct stage in the governed evolution of a data product.

### announcement
The product has been formally announced but is not yet available. This stage is typically used to signal intent and upcoming availability to stakeholders.

### draft
The product definition exists but is incomplete. It is not validated and not intended for consumption.

### development
The product is under active implementation. Technical realization and governance configuration are in progress.

### testing
The product is technically implemented and undergoing validation, quality checks, and controlled evaluation.

### acceptance
The product has passed testing and is awaiting formal approval or final validation before production release.

### production
The product is released and available to consumers under defined SLAs and governance commitments.

### sunset
The product is still available but marked for decommissioning. Consumers should prepare migration.

### retired
The product is no longer available and should not be used.

---

By aligning lifecycle states with ODPS, Maysano ensures interoperability, consistent governance semantics, and traceability across systems.


---

## 4. Roles and Accountability Boundaries

Maysano is built on clear separation of accountability. Collaboration is expected, but decision rights are not blurred.

Core roles typically include:

- **Product Manager**: defines intent, value, and alignment to business outcomes
- **Outcome Owner**: owns the business KPI and validates whether value is realized
- **Steward**: owns governance consistency and approves compliance to standards
- **Admin**: owns platform control, access, and operational configuration

The platform is designed so that each role has:

- a distinct set of actions
- clear decision boundaries
- an explicit trail of approvals and changes

---

## 5. Product Strategy

**Product Strategy** is the structured link between a data product and the business outcomes it serves.

In Maysano, strategy is expressed as:

- the business objective the product supports
- the KPI(s) used to measure success
- the target consumer group or value stream
- the rationale for why the product exists

This concept prevents “data products” from becoming technical artifacts without business justification.

---

## 6. Business Objective

A **Business Objective** defines what improvement the organization expects and why the data product exists. It is expressed in business language, not technical implementation language.

A strong objective includes:

- a clear intent (what should improve)
- a measurable KPI
- a baseline and a target (where possible)
- a timeframe or review cadence
- an accountable outcome owner

Objectives can be reused across multiple data products, allowing the organization to manage a portfolio of products contributing to the same business goal.

---

## 7. KPI (Key Performance Indicator)

A **KPI** is the measurable signal used to assess whether the data product is delivering value.

In Maysano, KPIs are first-class objects so they can be:

- defined once and reused
- linked to objectives and products
- tracked consistently
- reviewed across time windows

KPIs are business measures (e.g., satisfaction, conversion, efficiency, cost), not operational metrics (like pipeline duration).

---

## 8. Governance Component Library

A **Governance Component** is a reusable governance building block that can be attached to data products.

Instead of re-writing governance rules for every product, Maysano promotes composability through a governance library.

Typical components include:

- **Data Quality policy** (dimensions, rules, thresholds)
- **SLA** (availability, refresh frequency, incident response)
- **Data Access policy** (who can access, how, under what conditions)
- **Support model** (channels, response targets, escalation path)
- **License / Agreement terms** (usage rights, restrictions)

Components are defined once and reused many times to ensure consistency.

---

## 9. Policy vs. Evidence

Maysano separates what is *declared* from what is *observed*.

- **Policy** describes what should be true (rules, thresholds, commitments).
- **Evidence** shows what is actually true (measurements, logs, checks, incidents).

This separation is essential for operational governance, because governance is not documentation—it is continuously validated reality.

---

## 10. Quality Signal

A **Quality Signal** is a measurable indicator that reflects whether the product meets the declared quality policy.

Quality signals can include:
- completeness, validity, timeliness, consistency scores
- schema drift detection
- freshness checks
- failed rule counts and trend analysis

Signals are not static “certificates.” They are monitored indicators that change as the world changes.

---

## 11. Drift

**Drift** is any meaningful deviation between what was expected and what is happening now.

Drift can appear as:

- schema changes
- quality degradation
- SLA breaches
- consumer impact (e.g., breaking changes)
- objective misalignment (product no longer supports the KPI)

Maysano treats drift as something to surface early, not something to discover after failures.

---

## 12. Approval Gate

An **Approval Gate** is a decision checkpoint where a responsible role must explicitly approve before a product can move forward.

Examples:

- Steward approval before production release
- Outcome owner validation before declaring an objective “on track”
- Admin approval for sensitive access policy changes

Gates are designed to protect governance integrity without slowing down iteration.

---

## 13. Operating View

Maysano’s views are designed around how people work, not around how data is stored.

A typical product operating view brings together:

- the product strategy and objective
- governance components attached to the product
- current evidence (quality signals, incidents, drift)
- version history and change traceability
- role-relevant actions and approvals

This is what turns a “data asset” into an operational product.

---

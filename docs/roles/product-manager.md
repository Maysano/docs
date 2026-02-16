# Product Manager  
*(Canonical: Data Product Manager)*

The Product Manager in Maysano owns the **data product as a product**. This role is accountable for shaping the product into a coherent, measurable, and governable unit that can be operated and improved over time.

The Product Manager does not “just document” data. The role ensures the product delivers value, remains aligned to business outcomes, and can be governed consistently using reusable components.

---

## Role Essence

The Product Manager owns the **what** and the **how well** of a data product.

- **What** the data product is (scope, boundaries, composition, consumers, interfaces)
- **How well** it performs internally (internal KPIs, operational signals, improvement loop)

The Product Manager translates strategic intent into product structure, and ensures the product is ready for governance review and publishing.

---

## Core Accountability

The Product Manager is accountable for:

- Data product scope and structure
- Internal KPIs and measurable operational success
- Product version lifecycle (draft → review → published → next version)
- Component selection and reuse (DQ, SLA, Access, Pricing where applicable)
- Maintaining a product definition that is complete, consistent, and publishable

---

## Key Responsibilities

### 1) Define and maintain product structure

The Product Manager defines:

- product purpose and boundaries
- intended consumers and usage patterns
- key entities, metrics, and data semantics (business meaning)
- access patterns and delivery expectations (in collaboration with governance)

### 2) Link product to objectives and outcomes

The Product Manager ensures the product aligns with:

- the relevant business objective(s)
- the outcome KPI(s) defined by the Outcome Owner
- the internal KPIs that measure product execution performance

### 3) Define and maintain Internal KPIs

Internal KPIs are the Product Manager’s core instrument for steering execution, including:

- timeliness and refresh expectations
- completeness and coverage signals
- reliability and operational stability
- adoption/use signals (where measurable)

### 4) Select governance components (prefer reuse)

The Product Manager selects or requests:

- DQ profiles
- SLA profiles
- Access profiles
- Pricing profiles (if applicable)

The Product Manager should **prefer reuse** from the governance library and request new components only when necessary.

### 5) Manage product versions

The Product Manager drives version progression:

- create draft versions for change
- ensure changes are explicit and traceable
- prepare the version for governance review
- coordinate publishing readiness

---

## Explicit Non-Responsibilities

The Product Manager does not:

- Define business objectives or outcome KPIs (Outcome Owner responsibility)
- Approve governance components or templates (Steward responsibility)
- Own platform configuration and user access policy (Admin responsibility)
- Take responsibility for infrastructure operations (unless the organization assigns this separately)

---

## Decision Authority

The Product Manager has final decision authority over:

- Data product scope and structure
- Internal KPI definitions (and their evolution over time)
- When a product version is ready to submit for review/publishing
- What changes belong in which version

---

## Primary Outputs in Maysano

A Product Manager typically produces and maintains:

- Data product definition (ODPS-aligned structure)
- Product versions and change intent
- Internal KPIs linked to product execution
- Component references (DQ/SLA/Access/Pricing) selected from the governance library
- Product documentation for users (how to use, expectations, constraints)

---

## Collaboration Model

The Product Manager collaborates continuously with:

- **Outcome Owner**: confirm alignment to objectives and outcome KPIs; clarify priorities and trade-offs
- **Steward**: select governance components; request or refine reusable profiles; resolve governance gaps
- **Admin**: ensure correct access model and tenant-level configuration; resolve operational blockers
- **Engineering / Delivery roles (if present)**: ensure changes are shipped to production and adopted

---

## Interaction with AI

AI can accelerate Product Manager work by helping to:

- draft ODPS-aligned product specifications
- identify missing sections or inconsistencies
- propose internal KPI candidates and definitions
- suggest governance components from the library
- generate structured summaries for stakeholders

AI proposals must be reviewed and approved by the Product Manager. AI does not own product decisions.

---

## Success Indicators

A Product Manager is successful when:

- products remain aligned to outcomes and are measurable
- governance reuse increases over time (instead of fragmentation)
- internal KPIs are stable, meaningful, and tracked
- version changes are intentional, traceable, and publishable
- products are not “stuck in draft” and move to real use

# Roles Overview

Maysano is built around clear separation of accountability between business intent, product execution, governance integrity, and platform control.

The role model ensures that:

- Strategy is not confused with implementation.
- Product structure is not confused with governance standards.
- Governance consistency is not diluted by product pressure.
- Operational control remains independent of business logic.

Each role has a distinct decision boundary. Collaboration is expected. Accountability is not shared.

---

## The Role Model at a Glance

Maysano operates with four primary roles:

| Working Name      | Canonical Name                | Core Focus                     |
|------------------|-------------------------------|--------------------------------|
| Outcome Owner     | Business Outcome Owner        | Business objectives & success |
| Product Manager   | Data Product Manager          | Product structure & internal KPIs |
| Steward           | Data Product System Steward   | Governance library & standards |
| Admin             | Platform Administrator        | Platform configuration & access |

---

## Structural Separation of Concerns

The roles map to different layers of responsibility:

### 1. Strategic Layer — Outcome Owner

Defines **why** the organization invests in data products and how success is measured at the business level.

Owns:

- Objectives
- Outcome KPIs
- Strategic alignment

Does not own:

- Product design
- Governance components
- Implementation

---

### 2. Product Layer — Product Manager

Translates business objectives into structured, measurable data products.

Owns:

- Product scope
- Internal KPIs
- Product versions
- Component selection

Does not own:

- Business objectives
- Governance standards
- Platform configuration

---

### 3. Governance Layer — Steward

Ensures reusable governance components remain consistent, high quality, and scalable across products.

Owns:

- DQ profiles
- SLA profiles
- Access profiles
- Governance templates
- Component lifecycle

Does not own:

- Product scope
- Business outcomes
- Infrastructure

---

### 4. Platform Layer — Admin

Maintains operational integrity and secure platform configuration.

Owns:

- Access control
- Role assignments
- Tenant configuration
- Environment setup

Does not own:

- Business objectives
- Product structure
- Governance standards

---

## Why This Separation Matters

Without structural separation:

- Objectives drift.
- Products accumulate technical debt.
- Governance becomes inconsistent.
- Accountability becomes ambiguous.

Maysano enforces clarity by design. Each role has defined authority boundaries, enabling:

- Predictable governance
- Scalable reuse
- Clear decision ownership
- Measurable business alignment

---

## Human-in-Control Principle

AI supports every role by:

- Drafting proposals
- Highlighting gaps
- Suggesting reusable components
- Accelerating validation

However:

- AI does not own objectives.
- AI does not approve governance.
- AI does not deploy changes.
- AI does not assume accountability.

Final authority always rests with the designated role holder.

---

## Role Collaboration Model

Although accountability is separated, collaboration is continuous:

- Outcome Owner defines direction.
- Product Manager structures execution.
- Steward ensures governance integrity.
- Admin ensures operational stability.

This separation is what allows Maysano to scale governance without slowing down innovation.

# Access Controls

Maysano implements role-based access control (RBAC) to ensure that users can only perform actions appropriate to their organizational role. Every permission is explicitly defined, assigned, and enforceable.

---

## Role-Based Access Control

Maysano defines five core roles. Each role has a specific focus area and a fixed set of permissions. Users can hold multiple roles simultaneously.

### Core Roles

| Role | Focus Area | Operates At |
|---|---|---|
| **Outcome Owner** | Business objectives, outcome KPIs, strategic alignment | Enterprise / domain level |
| **Product Manager** | Product value, scope, priorities, product KPIs | Product level |
| **Product Owner** | Metadata, DQ implementation, tooling, operational signals | Product / operational level |
| **System Steward** | Governance integrity, component lifecycle, templates, AI guidance | Portfolio / system level |
| **Platform Admin** | Full platform access, user management, system configuration | Platform-wide |

---

## Permission Matrix

Each role has a defined set of 18 permissions:

| Permission | Outcome Owner | Product Manager | Product Owner | System Steward | Platform Admin |
|---|---|---|---|---|---|
| Define objectives | Yes | - | - | - | Yes |
| Manage outcome KPIs | Yes | - | - | - | Yes |
| Align products to objectives | Yes | Yes | - | - | Yes |
| Manage product KPIs | - | Yes | - | - | Yes |
| Manage product vision | - | Yes | - | - | Yes |
| Manage roadmap | - | Yes | - | - | Yes |
| Manage product metadata | - | - | Yes | - | Yes |
| Manage DQ rules | - | - | Yes | - | Yes |
| Manage product tooling | - | - | Yes | - | Yes |
| Define governance | - | - | - | Yes | Yes |
| Manage templates | - | - | - | Yes | Yes |
| Manage contracts | - | Yes | Yes | Yes | Yes |
| Manage AI guidance | - | - | - | Yes | Yes |
| View products | Yes | Yes | Yes | Yes | Yes |
| View dashboard | Yes | Yes | Yes | Yes | Yes |
| Manage users | - | - | - | Yes | Yes |
| Configure platform | - | - | - | Yes | Yes |
| Push to GitHub | - | Yes | - | Yes | Yes |

---

## RACI Matrix

Maysano defines responsibility boundaries using a RACI model across five activity areas:

### Strategy, Objectives, KPIs

| Activity | Outcome Owner | Product Manager | Product Owner | System Steward | Platform Admin |
|---|---|---|---|---|---|
| Define business objectives | R/A | C | I | I | R/A |
| Define outcome KPIs | R/A | C | I | I | R/A |
| Approve objective-product alignment | A | R | C | I | R/A |
| Define product KPIs | C | R/A | C | I | R/A |
| KPI pattern standardization | I | C | I | R/A | R/A |

### Data Product Design and Delivery

| Activity | Outcome Owner | Product Manager | Product Owner | System Steward | Platform Admin |
|---|---|---|---|---|---|
| Product vision and scope | C | R/A | C | I | R/A |
| Roadmap and prioritization | C | R/A | I | I | R/A |
| Product specification | I | C | R/A | I | R/A |
| Spec correctness and completeness | I | C | R/A | I | R/A |
| Day-to-day product hygiene | I | I | R/A | I | R/A |

### Governance Components and Templates

| Activity | Outcome Owner | Product Manager | Product Owner | System Steward | Platform Admin |
|---|---|---|---|---|---|
| Define governance principles | I | I | I | R/A | R/A |
| Create and evolve templates | I | C | C | R/A | R/A |
| Define DQ/SLA/Access profiles | I | C | C | R/A | R/A |
| Select profiles for a product | I | R | R | C | R/A |
| Governance drift management | I | I | C | R/A | R/A |

### AI-Assisted Workflows

| Activity | Outcome Owner | Product Manager | Product Owner | System Steward | Platform Admin |
|---|---|---|---|---|---|
| AI objective exploration | R/A | C | I | I | R/A |
| AI-assisted spec generation | I | R | R | C | R/A |
| AI guardrails and guidance | I | I | I | R/A | R/A |
| Review AI-generated outputs | I | C | R/A | C | R/A |

**Legend:** R = Responsible, A = Accountable, C = Consulted, I = Informed, R/A = Responsible and Accountable

---

## Multi-Role Support

Users can hold multiple roles simultaneously. Permissions are additive — a user with both Product Manager and Product Owner roles has the combined permissions of both.

The Platform Admin role is a superset of all permissions. It is intended for system administrators who need unrestricted access.

---

## What Access Controls Do Not Do

- **Do not control data access.** RBAC controls what users can do in the Maysano platform. Access to underlying data is controlled by the data infrastructure.
- **Do not enforce workflow sequences.** Permissions control actions, not order. A user with the right permission can perform any allowed action at any time.
- **Do not replace organizational hierarchy.** Roles in Maysano are functional, not organizational. A senior manager may hold the Outcome Owner role; a junior analyst may hold the Product Owner role.

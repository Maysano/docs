# Pricing Plans

Pricing Plans in Maysano declare the commercial model for a data product. They define how consumers are charged, what is included, and what happens when usage exceeds included limits.

---

## What Pricing Plans Define

A Pricing Plan is a governance component that captures the commercial terms of a data product. It answers:

- What pricing model applies? (flat, per-use, tiered, freemium)
- What does it cost?
- What is the billing cycle?
- What is included?
- What happens when limits are exceeded?

---

## Profile Structure

| Field | Description | Example Values |
|---|---|---|
| `name` | Human-readable plan name | "Enterprise Plan", "Pay-As-You-Go" |
| `description` | Purpose and scope | "Usage-based pricing for external consumers" |
| `pricingModel` | Pricing strategy | `flat`, `per_use`, `tiered`, `freemium` |
| `currency` | Billing currency | `USD`, `EUR`, `GBP` |
| `price` | Base price | `99.00`, `0.01` |
| `billingPeriod` | Billing cycle | `monthly`, `quarterly`, `yearly` |
| `usageUnit` | Unit for per-use pricing | `api_call`, `row`, `GB`, `query` |
| `includedUnits` | Units included in the base price | `10000`, `1000000` |
| `overageRate` | Cost per unit beyond included limit | `0.001` |
| `features` | List of included features | `["real-time access", "SLA support", "priority queue"]` |
| `version` | Semantic version | `1.0.0` |
| `lifecycle` | Current lifecycle state | `draft`, `production`, `retired` |
| `isDefault` | Default plan for new products | `true` / `false` |

---

## Pricing Models

| Model | Description |
|---|---|
| **Flat** | Fixed price per billing period regardless of usage. Simple and predictable. |
| **Per-use** | Charged per unit of consumption (API calls, rows, GB). Scales with usage. |
| **Tiered** | Multiple pricing levels based on volume. Lower per-unit cost at higher volumes. |
| **Freemium** | Free base tier with premium features or higher limits available for a fee. |

---

## Plan Features

The `features` field is a list of capabilities included in the plan. This allows differentiation between tiers:

- A free tier might include `["read-only access", "100 queries/day"]`
- An enterprise tier might include `["real-time access", "SLA support", "dedicated endpoint", "priority queue"]`

Features are descriptive labels. They communicate what is included but do not enforce access to those features — enforcement is handled by the product infrastructure.

---

## Lifecycle and Versioning

Pricing Plans follow the standard governance component lifecycle:

**draft** → **development** → **testing** → **acceptance** → **production** → **sunset** → **retired**

Version increments follow semantic versioning. Published product versions capture the exact Pricing Plan version at the time of release.

---

## Attaching Pricing Plans to Products

A data product can reference one or more Pricing Plans. Multiple plans per product enable tiered offerings (e.g. free, standard, enterprise).

---

## What Pricing Plans Do Not Do

- **Do not process payments.** Pricing Plans declare terms; billing systems collect payments.
- **Do not enforce usage limits.** The plan declares `10000 API calls/month`; the API gateway enforces it.
- **Do not track consumption.** Usage metering is an infrastructure concern.
- **Do not replace contracts.** Pricing Plans are internal governance artifacts. External commercial agreements may reference them but are managed separately.

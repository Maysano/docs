# Service Level Agreements (SLA)

SLA Profiles in Maysano declare the service-level commitments a data product makes to its consumers. They define measurable expectations for availability, performance, and support — aligned with the ODPS 4.1 standard.

---

## What SLA Means in Maysano

An SLA Profile is a **policy artifact**. It declares what a data product commits to delivering in terms of availability, performance, and responsiveness. It does not monitor or enforce these commitments — that is the responsibility of operational tooling.

Maysano separates the commitment (SLA Profile) from the evidence (monitoring, alerting, incident tracking). This ensures that governance intent is captured independently of operational implementation.

---

## The Eleven SLA Dimensions

Maysano defines eleven standardized SLA dimensions based on the ODPS 4.1 specification.

| Dimension | Definition | Example Value |
|---|---|---|
| **Latency** | Minimal amount of time before getting any response | `< 200ms` |
| **Uptime** | Percentage of time the system is working and available | `99.9%` |
| **Response Time** | Amount of time to process an external request | `< 500ms` |
| **Error Rate** | Maximum tolerated errors in data, expressed as a percentage | `< 0.1%` |
| **End of Support** | The date at which the product will no longer have support | `2026-12-31` |
| **End of Life** | The date at which the product will no longer be available | `2027-06-30` |
| **Update Frequency** | How often data is updated | `hourly` |
| **Time to Detect** | How fast a problem can be detected | `< 5 minutes` |
| **Time to Notify** | Time needed to notify users once a problem is detected | `< 15 minutes` |
| **Time to Repair** | Time needed to fix an issue once detected | `< 4 hours` |
| **Email Response Time** | Time needed to respond to email support requests | `< 24 hours` |

Not every dimension needs a value. A product may commit to uptime and update frequency without specifying email response time. Unfilled dimensions indicate that no commitment is made for that aspect.

---

## SLA Profiles

An SLA Profile is a reusable governance component that bundles dimension commitments into a named, versioned artifact.

### Profile Structure

| Field | Description |
|---|---|
| `name` | Human-readable profile name (e.g. "Gold SLA", "Standard SLA") |
| `description` | Purpose and scope of the profile |
| `latency` | Latency commitment |
| `uptime` | Uptime commitment |
| `responseTime` | Response time commitment |
| `errorRate` | Error rate commitment |
| `endOfSupport` | Support end date |
| `endOfLife` | End of life date |
| `updateFrequency` | Data update frequency |
| `timeToDetect` | Detection time commitment |
| `timeToNotify` | Notification time commitment |
| `timeToRepair` | Repair time commitment |
| `emailResponseTime` | Email response time commitment |
| `version` | Semantic version |
| `lifecycle` | Current lifecycle state |
| `isDefault` | Whether this is the default SLA for new products |

### Example Profiles

**Gold SLA** — For business-critical products:

- Uptime: 99.9%
- Latency: < 100ms
- Update Frequency: real-time
- Time to Detect: < 1 minute
- Time to Repair: < 1 hour

**Standard SLA** — For internal operational products:

- Uptime: 99.5%
- Update Frequency: daily
- Time to Detect: < 30 minutes
- Time to Repair: < 8 hours

---

## Policy vs Evidence

An SLA Profile states what a product commits to. It does not verify whether the commitment is being met. That verification happens through:

- Infrastructure monitoring (uptime, latency)
- Data pipeline observability (update frequency, freshness)
- Incident management (time to detect, repair, notify)

Maysano captures the commitment. The operational stack captures the evidence. This separation ensures that SLA definitions remain stable even as monitoring tools change.

---

## Lifecycle and Versioning

SLA Profiles follow the standard governance component lifecycle:

**draft** → **development** → **testing** → **acceptance** → **production** → **sunset** → **retired**

When an SLA Profile is updated, its version is incremented. Products referencing a specific version retain that reference. A published product version captures the exact SLA Profile version it was released with.

---

## Attaching SLAs to Products

A data product references an SLA Profile by ID. The attachment is recorded at the product level and captured in each published version.

Multiple products can share the same SLA Profile. This ensures consistent commitments across the portfolio without duplicating definitions.

---

## What SLA Does Not Do

- **Does not monitor uptime or latency.** SLA Profiles are declarations, not monitoring agents.
- **Does not trigger alerts.** Alerting is the responsibility of operational tooling.
- **Does not auto-enforce.** A breached SLA does not automatically change product status. Enforcement is a governance decision.
- **Does not replace contracts.** SLA Profiles are internal governance artifacts. External contractual SLAs may reference them but are managed separately.

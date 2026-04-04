# Versioning Model

Maysano uses semantic versioning throughout the platform to track changes to data products and governance components. This page describes how versioning works and what immutability guarantees it provides.

---

## Semantic Versioning

All versioned artifacts in Maysano follow the semantic versioning convention: `MAJOR.MINOR.PATCH`.

| Segment | Meaning |
|---|---|
| **Major** | Breaking changes that may require consumers to adapt |
| **Minor** | New capabilities or relaxed constraints; backward compatible |
| **Patch** | Corrections, clarifications, or metadata updates |

---

## Product Versioning

Data products support full version management:

### Creating a Version

When a product owner publishes a version:

1. A version number is assigned (auto-incremented or manually specified).
2. A `changeDescription` documents what changed.
3. An immutable snapshot is created.

### What the Snapshot Captures

| Field | Description |
|---|---|
| `version` | The semantic version string |
| `specification` | Complete ODPS specification (JSON) |
| `yamlSpec` | ODPS specification in YAML |
| `changeDescription` | Human-readable description of changes |
| `slaId` | SLA Profile reference at time of publication |
| `dataQualityId` | DQ Profile reference at time of publication |
| `accessProfileId` | Access Profile reference at time of publication |
| `status` | Product lifecycle state at publication |
| `name` | Product name at publication |
| `description` | Product description at publication |
| `type` | Product type at publication |
| `visibility` | Product visibility at publication |
| `owner` | Product owner at publication |
| `tags` | Product tags at publication |
| `productStrategy` | Strategy (objectives, KPIs) at publication |

### Immutability

Once published, a version snapshot cannot be modified. This is a core governance guarantee:

- You can always reconstruct the exact state of a product at any version.
- Governance component references are frozen — updating a DQ Profile does not retroactively change published versions.
- Audit trails remain intact.

To make changes, a new version must be created.

---

## Governance Component Versioning

Each governance component (DQ Profile, SLA Profile, Access Profile, Pricing Plan) carries its own version:

| Field | Description |
|---|---|
| `version` | Semantic version (e.g. `1.0.0`) |
| `lifecycle` | Current lifecycle state |

### Version Increment Rules

- Updating a component's values increments the version.
- The version is tracked independently of the products that reference the component.
- Products reference the component by ID; the version at the time of product publication is captured in the version snapshot.

### Component-Product Relationship

When a product is published, the governance component versions are captured. If the component is later updated to a new version:

- Existing published product versions still reference the old component version.
- The live (unpublished) product can be updated to reference the new component version.
- A new product version must be published to capture the updated component reference.

---

## Guidance Ruleset Versioning

Guidance rulesets are immutable, versioned snapshots of AI guidance rules:

| Field | Description |
|---|---|
| `version` | Semantic version |
| `rules` | Array of frozen rule snapshots |
| `ruleCount` | Number of rules in the snapshot |
| `isActive` | Whether this ruleset is the active one |

Only one ruleset can be active at a time. Publishing a new ruleset does not delete previous ones — they are preserved for audit and rollback.

---

## Immutability Guarantees

| Artifact | Mutable? | Notes |
|---|---|---|
| Product (draft) | Yes | Can be freely edited before publishing |
| Product (published version) | No | Snapshot is frozen at publication time |
| Governance component | Yes | Can be updated; version increments |
| Component reference in published version | No | Captured at publication time |
| Guidance ruleset | No | Each published ruleset is immutable |
| Activity logs | No | Append-only audit trail |
| Structural events | No | Append-only event log |

---

## What the Versioning Model Does Not Do

- **Does not enforce backward compatibility.** Semantic versioning communicates intent, but the platform does not block breaking changes.
- **Does not auto-migrate consumers.** When a product publishes a new major version, consumers must update their references manually.
- **Does not limit version count.** There is no maximum number of versions for a product or component.
- **Does not provide diff views.** Version comparison is done at the metadata level, not through visual diff tooling.

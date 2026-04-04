# Access Profiles

Access Profiles in Maysano declare how a data product can be accessed by its consumers. They define the authentication method, data format, communication protocol, and rate limits — standardized as reusable governance components.

---

## What Access Profiles Define

An Access Profile is a policy artifact that answers four questions about product access:

1. **How do consumers authenticate?** (authentication method)
2. **What format is the data delivered in?** (data format)
3. **What protocol is used?** (communication protocol)
4. **How much access is allowed?** (rate limiting)

These declarations ensure that access patterns are consistent across the portfolio and clearly communicated to consumers.

---

## Profile Structure

| Field | Description | Example Values |
|---|---|---|
| `name` | Human-readable profile name | "Public API Access", "Internal Read-Only" |
| `description` | Purpose and scope | "Standard access profile for external API consumers" |
| `authMethod` | Authentication method | `api_key`, `oauth2`, `basic`, `bearer_token`, `none` |
| `format` | Data delivery format | `json`, `csv`, `parquet`, `xml`, `avro` |
| `protocol` | Communication protocol | `rest`, `graphql`, `grpc`, `websocket`, `sftp` |
| `rateLimit` | Maximum request rate | `1000/hour`, `100/minute`, `unlimited` |
| `version` | Semantic version | `1.0.0` |
| `lifecycle` | Current lifecycle state | `draft`, `production`, `retired` |
| `isDefault` | Default profile for new products | `true` / `false` |

---

## Authentication Methods

The `authMethod` field declares the expected authentication mechanism:

| Method | Use Case |
|---|---|
| `api_key` | Simple token-based access for programmatic consumers |
| `oauth2` | Delegated authorization for third-party applications |
| `basic` | Username/password authentication (internal use) |
| `bearer_token` | Token-based authentication via Authorization header |
| `none` | Public, unauthenticated access |

The Access Profile declares the method. The implementation of that method (token generation, OAuth flow, etc.) is handled by the infrastructure layer.

---

## Rate Limiting

Rate limits protect products from overuse and ensure fair access across consumers. The `rateLimit` field is a human-readable declaration (e.g. `1000/hour`) that communicates the expected throughput constraint.

Rate limiting is declared in the profile and enforced by the API gateway or infrastructure layer. Maysano captures the commitment; the operational stack enforces it.

---

## Lifecycle and Versioning

Access Profiles follow the standard governance component lifecycle:

**draft** → **development** → **testing** → **acceptance** → **production** → **sunset** → **retired**

Version increments follow semantic versioning. A published product version captures the exact Access Profile version it was released with.

---

## Attaching Access Profiles to Products

A data product references an Access Profile by ID. The attachment is recorded at the product level and included in published version snapshots.

Multiple products can share the same Access Profile. This ensures consistent access patterns for products with similar consumer requirements.

---

## What Access Profiles Do Not Do

- **Do not implement authentication.** The profile declares `oauth2`; the infrastructure implements the OAuth flow.
- **Do not enforce rate limits.** The profile declares `1000/hour`; the API gateway enforces it.
- **Do not manage credentials.** API keys, tokens, and secrets are managed by the identity and access management layer, not by Maysano.
- **Do not control network access.** Firewall rules, VPNs, and network policies are infrastructure concerns.

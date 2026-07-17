# Architecture Decision Log

This document captures key architecture decisions for the GCC High secure collaboration reference architecture.

## ADR-001: Use dedicated collaboration boundaries

**Status:** Accepted

### Context

External collaboration must be controlled, auditable, and easy to review. Broad tenant-level sharing increases operational and security risk.

### Decision

Use dedicated SharePoint Online sites or Microsoft Teams workspaces for approved partner collaboration scenarios.

### Rationale

Dedicated collaboration boundaries make it easier to scope permissions, apply governance, review access, and remove collaboration access when the business need ends.

### Consequences

- More planning is required before external users are added.
- Access is easier to review and remove.
- Collaboration workspaces can be aligned to business purpose, partner, or project.

---

## ADR-002: Use Microsoft Entra B2B Collaboration for external identities

**Status:** Accepted

### Context

External users need access to selected Microsoft 365 resources without creating unmanaged local identities by default.

### Decision

Use Microsoft Entra B2B Collaboration as the primary external identity pattern for approved collaboration users.

### Rationale

This approach supports scoped access to Microsoft 365 resources while preserving separation between Client Alpha and partner organizations.

### Consequences

- Guest user lifecycle must be governed.
- External collaboration settings must be reviewed.
- Conditional Access, MFA, and licensing assumptions must be validated.

---

## ADR-003: Use group-based access control

**Status:** Accepted

### Context

Direct user permissions can become difficult to manage as external collaboration grows.

### Decision

Assign external user access through dedicated security groups whenever possible.

### Rationale

Group-based access improves lifecycle management, supports access reviews, and reduces permission sprawl.

### Consequences

- Groups require ownership and naming standards.
- Access reviews must include group membership validation.
- Support teams need a documented process for onboarding and offboarding.

---

## ADR-004: Validate sensitivity label behavior before rollout

**Status:** Accepted

### Context

Sensitivity labels, encryption, and external access behavior may vary based on tenant configuration, label policy, licensing, and user access conditions.

### Decision

Do not assume protected document collaboration will work consistently across tenants until validated through structured testing.

### Rationale

Testing reduces deployment risk and helps define the expected user experience before production rollout.

### Consequences

- A test plan is required before broad enablement.
- Label behavior must be validated for browser access, desktop access, co-authoring, download restrictions, and external users.
- Any limitations should be documented clearly for business and support teams.

---

## ADR-005: Start with a controlled pilot

**Status:** Accepted

### Context

The architecture includes multiple dependency areas, including identity, licensing, SharePoint, Teams, Purview labels, Conditional Access, and endpoint behavior.

### Decision

Start with a small pilot group, limited collaboration scope, and non-sensitive test content before expanding usage.

### Rationale

A pilot allows the team to validate assumptions, identify limitations, and refine governance before broader rollout.

### Consequences

- Initial rollout is slower but lower risk.
- Pilot results inform final design decisions.
- Support documentation can be improved before broader adoption.

# Constraints

## Environment Constraints

- The architecture is designed for Microsoft 365 GCC High environments.
- Each organization operates its own Microsoft 365 tenant.
- Tenant configurations may differ between organizations.
- External collaboration must preserve tenant boundaries.
- Feature availability and behavior must be validated in GCC High before implementation.

## Identity Constraints

- External users belong to separate organizations.
- External users may authenticate through their own home tenant.
- Guest access must be explicitly granted and governed.
- External users should not receive broad access to internal resources.
- Group-based access should be preferred over direct user assignment.

## Licensing Constraints

- Collaboration capabilities may depend on licensing in each participating tenant.
- Sensitivity label, encryption, compliance, and access capabilities may vary by license.
- Licensing assumptions must be validated before final architecture approval.
- Unsupported or unavailable capabilities should not be treated as design dependencies.

## Data Protection Constraints

- Sensitivity labels may be configured differently across organizations.
- Label names, policies, encryption settings, and permissions may not align between tenants.
- Protected documents may behave differently for external users depending on label configuration.
- Sensitivity label behavior must be tested before production rollout.
- Data access should be limited to approved business purposes.

## Collaboration Constraints

- SharePoint Online access must be scoped to approved sites, libraries, folders, or files.
- Microsoft Teams collaboration should be restricted to approved teams or channels.
- Co-authoring behavior must be validated with external users.
- Browser-based and desktop application experiences may differ.
- External sharing should not bypass compliance or security policies.

## Operational Constraints

- Access reviews must be practical for support teams to manage.
- External user onboarding and offboarding must be documented.
- Support teams must understand ownership of users, groups, sites, labels, and policies.
- Audit logs and access activity should be reviewed where available.
- The architecture should be implemented in phases, starting with a controlled pilot.

## Assumptions

- Only approved external users require access.
- Collaboration will be scoped to specific business scenarios.
- Microsoft-native controls are preferred where available.
- Sensitive content requires classification and protection.
- Final implementation depends on licensing, feature availability, security review, and validation testing.
# Collaboration Patterns

## Purpose

This document compares collaboration patterns for a regulated organization operating in Microsoft 365 GCC High that needs to collaborate securely with external partner organizations.

The goal is to enable controlled document collaboration, Microsoft Teams collaboration, and protected content sharing while preserving compliance, least privilege access, and operational governance.

## Scenario Summary

Client Alpha operates in Microsoft 365 GCC High and collaborates with external partner organizations that may also operate in regulated Microsoft 365 environments.

The collaboration model must support:

- Approved external user access
- SharePoint Online document collaboration
- Microsoft Teams collaboration
- Protected document handling
- Microsoft Purview sensitivity label validation
- Conditional Access and MFA enforcement
- Licensing and feature availability validation
- Access review and offboarding governance

## Collaboration Pattern Options

| Pattern | Description | When to Use | Key Considerations |
|---|---|---|---|
| Microsoft Entra B2B Collaboration | Invite approved external users into Client Alpha as guest users for scoped access to Microsoft 365 resources. | Targeted collaboration with specific external users, SharePoint sites, Teams, or documents. | Requires governance for guest lifecycle, access reviews, Conditional Access, and licensing validation. |
| SharePoint Online External Sharing | Share site, library, folder, or file access with approved external users. | Document collaboration, proposal work, file review, and controlled co-authoring. | Access should be scoped carefully. Sharing settings, link types, permissions, and download restrictions must be reviewed. |
| Microsoft Teams Guest Collaboration | Add approved external users to Teams where collaboration requires chat, meetings, files, and shared workspace access. | Ongoing project collaboration with external users. | Teams file access is backed by SharePoint Online, so site permissions and guest access governance must align. |
| Dedicated Collaboration Site | Create a dedicated SharePoint site for each partner or project collaboration scenario. | When collaboration needs clear boundaries, easier review, and clean offboarding. | Recommended pattern for controlled collaboration because access can be isolated and reviewed more easily. |
| Group-Based Access | Assign permissions through dedicated security groups rather than direct user permissions. | Repeatable external access management and access reviews. | Improves governance and reduces manual permission sprawl. Requires group ownership and review cadence. |
| Sensitivity Label Protected Collaboration | Apply Microsoft Purview sensitivity labels to classify and protect documents shared with external users. | Sensitive or regulated content collaboration. | Label encryption, external user access, co-authoring, and download behavior must be tested before rollout. |
| Browser-Based Collaboration First | Start external collaboration testing through browser-based Microsoft 365 experiences. | Initial pilot and validation phase. | Helps reduce endpoint variability during testing. Desktop application behavior should be validated separately. |
| Manual File Exchange | Users exchange files through email attachments or unmanaged transfer methods. | Only as an exception or temporary fallback. | Not recommended for regulated collaboration because governance, auditability, and version control are weaker. |

## Recommended Pattern

The recommended collaboration model is a governed Microsoft 365 collaboration boundary:

1. Create a dedicated SharePoint Online site or Team for each approved collaboration scenario.
2. Invite external users through Microsoft Entra B2B Collaboration.
3. Assign access through dedicated security groups.
4. Apply Conditional Access and MFA requirements.
5. Apply Microsoft Purview sensitivity labels based on data classification.
6. Validate document behavior across browser, desktop, co-authoring, and download scenarios.
7. Review access periodically and remove external users when no longer required.

## Key Architecture Principle

Secure collaboration in Microsoft 365 GCC High should not be treated as a simple sharing configuration. It requires coordinated decisions across identity, SharePoint, Teams, sensitivity labels, licensing, device access, monitoring, and governance.

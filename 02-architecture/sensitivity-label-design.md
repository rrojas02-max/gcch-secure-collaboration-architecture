# Sensitivity Label Design

## Purpose

This document describes the sensitivity label design considerations for secure external collaboration in Microsoft 365 GCC High.

The goal is to protect regulated content while allowing approved external users to collaborate where business requirements and compliance controls allow.

## Design Goals

The sensitivity label design should support the following goals:

- Classify content based on sensitivity and business purpose.
- Protect sensitive documents shared with approved external users.
- Validate external user access to labeled and encrypted content.
- Reduce accidental oversharing.
- Support auditability and governance.
- Document expected behavior and limitations before rollout.

## Label Design Considerations

### 1. Label taxonomy

Client Alpha should use a simple and understandable label structure that users can apply consistently.

Example label categories:

- Public
- Internal
- Confidential
- Regulated
- Highly Restricted

The exact label names should be defined by the organization’s compliance and data governance teams.

### 2. External collaboration labels

Not every label should allow external collaboration.

Recommended approach:

| Label Type | External Sharing Recommendation |
|---|---|
| Public | Sharing may be allowed based on business policy. |
| Internal | External sharing generally restricted. |
| Confidential | External sharing only with approved users and business justification. |
| Regulated | External sharing requires validation, approval, and access controls. |
| Highly Restricted | External sharing not allowed unless explicitly approved by security and compliance teams. |

### 3. Encryption and permissions

For labels that apply encryption, the design must validate whether approved external users can:

- Open protected documents.
- Edit protected documents.
- Co-author documents.
- Access documents through browser-based Microsoft 365.
- Access documents through desktop Office applications.
- Download or synchronize protected content.
- Retain access after being removed from the collaboration group.

### 4. Partner tenant differences

Partner organizations may have different tenant configurations, label names, policies, licensing, endpoint controls, and access conditions.

Because of this, Client Alpha should not assume that sensitivity labels align automatically across organizations.

### 5. Testing approach

Before rollout, test each approved collaboration scenario using non-sensitive sample content.

Recommended test cases:

- External user opens unlabeled document.
- External user opens labeled but unencrypted document.
- External user opens encrypted document.
- External user edits document in browser.
- External user edits document in desktop application.
- External user attempts co-authoring.
- External user attempts download.
- External user access is removed and retested.
- Label changed after sharing and access behavior retested.

## Recommended Label Governance

Client Alpha should define:

- Who owns sensitivity label policies.
- Which labels allow external collaboration.
- Which groups are allowed to access protected content.
- What approval is required before content is shared externally.
- How exceptions are documented.
- How access is reviewed.
- How support teams troubleshoot external access issues.

## Architecture Principle

Sensitivity labels are not only a compliance control. In external collaboration scenarios, they also become part of the access experience. Label behavior must be validated with identity, licensing, devices, SharePoint permissions, and user workflow before production rollout.

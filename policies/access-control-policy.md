# Access Control Policy — 01: On-Prem AD Simulation (EC2) to Okta Identity Bridge

**Classification:** Internal Use - Portfolio Demonstration
**Policy Owner:** Identity & Access Management (IAM) Engineering
**Effective Date:** 2026-08-16
**Review Cycle:** Annual
**Version:** 1.0

## 1. Purpose

This policy establishes the mandatory controls governing the architecture described in "On-Prem AD Simulation (EC2) to Okta Identity Bridge", in support of the compliance obligations listed in Section 6 and the risk position documented in the associated Compliance Mapping.

## 2. Scope

This policy applies to all personnel, systems, and third parties with access to the in-scope environment: EC2, VPC, Windows Server AD DS, Okta AD Agent. It applies regardless of employment classification (employee, contractor, or third party) where such access is technically possible.

## 3. Policy Statements

1. Active Directory shall remain the single authoritative source of identity truth for all in-scope users and groups for the duration of the hybrid bridge period.
2. No identity attribute shall be writable from Okta back into Active Directory without a documented, approved change request.
3. Synchronization health between Active Directory and Okta Universal Directory shall be monitored continuously, with alerting on sync failure exceeding fifteen (15) minutes.
4. Cutover to Okta as authoritative source, if ever proposed, shall require a formal risk assessment and sign-off from the IAM Engineering control owner.
5. All access reviews performed prior to go-live shall be evidenced and retained for a minimum of three (3) years in support of ISO 27001 A.9.1/A.9.2 audit requirements.

## 4. Roles & Responsibilities

| Role | Responsibility |
|---|---|
| Identity & Access Management (IAM) Engineering | Owns this policy, approves exceptions, and is accountable for control testing outcomes. |
| System/Application Owner | Ensures the in-scope system is configured in accordance with this policy at all times. |
| Requesting Individual | Complies with the access request and justification process defined in this policy. |
| Internal Audit / Compliance | Independently verifies control operating effectiveness per the testing procedure in `compliance/compliance-mapping.md`. |

## 5. Exceptions

Any deviation from the policy statements in Section 3 requires a documented, time-bound exception, approved in writing by Identity & Access Management (IAM) Engineering, with a defined expiry date and a compensating control where applicable. Exceptions shall be logged and reviewed at each policy review cycle.

## 6. Related Standards & Requirements

- ISO 27001 A.9.1 - Business requirements of access control
- ISO 27001 A.9.2 - User access management

## 7. Enforcement

Non-compliance with this policy is treated as a control deficiency and shall be logged, tracked, and remediated per the Non-Conformance Handling process defined in `compliance/compliance-mapping.md`. Repeated or willful non-compliance may result in access revocation pending review.

## 8. Document Control

| Version | Date | Author | Change Summary |
|---|---|---|---|
| 1.0 | 2026-08-16 | Identity & Access Management (IAM) Engineering | Initial approved version. |

---

[⬅ Back to project README](../README.md)

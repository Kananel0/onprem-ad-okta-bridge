# Architecture Decision Record — 01: On-Prem AD Simulation (EC2) to Okta Identity Bridge

**Status:** Accepted
**Date:** 2026-08-16
**Decider(s):** Identity & Access Management (IAM) Engineering
**Classification:** Internal Use - Portfolio Demonstration

## Context

Migrating from on-prem AD to cloud SSO without lift-and-shift, needing an audit trail proving access controls meet ISO 27001 before go-live.

The control owner evaluated the exposure against the in-scope compliance requirements (ISO 27001 A.9.1, ISO 27001 A.9.2) and determined that the existing state did not provide a defensible, auditable control.

## Decision

1. Deployed Windows Server AD DS on an EC2 instance inside a private VPC subnet, simulating an on-prem datacenter without physical hardware.
2. Installed the Okta AD Agent to sync users and groups from AD into Okta Universal Directory.
3. Configured Okta as the SSO broker for downstream applications while keeping AD as the sole system of record.

## Alternatives Considered

**Alternative: Full lift-and-shift cutover to a cloud-only directory on day one**
Rejected. Removes the ability to fall back to AD during migration and eliminates the audit trail needed to evidence access controls before go-live.

**Alternative: Federate directly from a newly created cloud directory with no bridge**
Rejected. Would require re-establishing every access review and control mapping from zero, with no continuity of identity history.

## Consequences

**Positive:**
- The control directly closes the exposure described in the Context section.
- The design produces an audit trail sufficient to evidence the compliance requirements in scope, without relying on manual, after-the-fact documentation.

**Negative / Residual Risk:**
Low. AD remains the sole authoritative source during the bridge period; Okta operates strictly as a consuming service. Residual risk is limited to sync-latency windows between AD changes and Okta reflection, which is monitored and alerted.

**Operational impact:**
Ownership of this control rests with Identity & Access Management (IAM) Engineering. Any change to the architecture described above requires this ADR to be revised and re-approved before the change is implemented in a production-equivalent environment.

---

[⬅ Back to project README](../README.md)

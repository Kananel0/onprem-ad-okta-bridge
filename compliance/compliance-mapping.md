# Compliance Mapping — 01: On-Prem AD Simulation (EC2) to Okta Identity Bridge

**Classification:** Internal Use - Portfolio Demonstration
**Control Owner:** Identity & Access Management (IAM) Engineering
**Testing Frequency:** Annual (or per the cadence stated in the governing policy, where more frequent)

## Control Objectives

| Requirement | Description |
|---|---|
| ISO 27001 A.9.1 | Business requirements of access control |
| ISO 27001 A.9.2 | User access management |

## Implementation Narrative

- Deployed Windows Server AD DS on an EC2 instance inside a private VPC subnet, simulating an on-prem datacenter without physical hardware.
- Installed the Okta AD Agent to sync users and groups from AD into Okta Universal Directory.
- Configured Okta as the SSO broker for downstream applications while keeping AD as the sole system of record.

## Control Testing Procedure

The following steps constitute the minimum testing procedure to be performed by the control owner, or by internal/external audit, to assess operating effectiveness:

1. Confirm AD DS replication health and Okta AD Agent connectivity status.
2. Sample ten (10) user/group changes in AD and verify reflection in Okta Universal Directory within SLA.
3. Attempt to modify a synced attribute directly in Okta; confirm the change is rejected or does not propagate back to AD.

## Evidence Artifacts

The following evidence shall be retained and made available on request to support control testing:

- Okta AD Agent health dashboard export
- AD replication status report (repadmin /replsummary)
- Sync exception/error log for the audit period

## Risk Assessment

**Inherent risk:** Uncontrolled or undocumented directory migration could result in loss of authoritative identity data, inconsistent access decisions during cutover, or an inability to demonstrate access-control lineage during an ISO 27001 surveillance audit.

**Residual risk (control in place):** Low. AD remains the sole authoritative source during the bridge period; Okta operates strictly as a consuming service. Residual risk is limited to sync-latency windows between AD changes and Okta reflection, which is monitored and alerted.

## Non-Conformance Handling

Any control testing result that fails one or more steps above shall be logged as a non-conformance, assigned to Identity & Access Management (IAM) Engineering, and remediated on a timeline commensurate with the residual risk rating. Non-conformances open longer than thirty (30) days shall be escalated per the organization's risk acceptance process.

---

[⬅ Back to project README](../README.md)

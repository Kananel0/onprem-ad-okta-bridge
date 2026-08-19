# Evidence Capture Checklist — On-Prem AD Simulation (EC2) to Okta Identity Bridge

**Classification:** Internal Use - Portfolio Demonstration

This repository does not ship fabricated or placeholder screenshots. Capture the following directly from the live environment (or a controlled lab reproduction), redact tenant IDs / real usernames / internal IPs, and commit them to this folder using the suggested file names.

## Step 1
- **What it shows:** Deployed Windows Server AD DS on an EC2 instance inside a private VPC subnet, simulating an on-prem datacenter without physical hardware.
- **Suggested filename:** `01-onprem-ad-okta-bridge-step1.png`

## Step 2
- **What it shows:** Installed the Okta AD Agent to sync users and groups from AD into Okta Universal Directory.
- **Suggested filename:** `02-onprem-ad-okta-bridge-step2.png`

## Step 3
- **What it shows:** Configured Okta as the SSO broker for downstream applications while keeping AD as the sole system of record.
- **Suggested filename:** `03-onprem-ad-okta-bridge-step3.png`

## Evidence Artifacts (from compliance/compliance-mapping.md)
- [ ] Okta AD Agent health dashboard export
- [ ] AD replication status report (repadmin /replsummary)
- [ ] Sync exception/error log for the audit period

## Optional Extras
- [ ] Before/after comparison (e.g. configuration state pre- and post-change)
- [ ] Relevant audit log entry proving the control fired as designed
- [ ] Screenshot of the control testing procedure being executed (per compliance/compliance-mapping.md)
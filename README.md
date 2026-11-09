# Enterprise IT Support Infrastructure & Advanced Troubleshooting Lab

> Advanced hands-on enterprise IT support lab focused on Windows Server administration, Active Directory, DNS, Group Policy, networking, access control, remote support, security hardening, performance troubleshooting, enterprise-style incident troubleshooting, and backup & recovery.

## Executive Summary

This project documents the design, administration, troubleshooting, hardening, and recovery of a Windows enterprise-style lab environment built to develop practical IT Support and systems troubleshooting skills.

The project goes beyond basic configuration. It focuses on diagnosing controlled incidents through evidence-based troubleshooting, identifying the failure domain and root cause, applying the minimum appropriate remediation, and verifying service restoration.

The lab was completed through nine technical phases with 66 evidence artifacts documenting configuration, troubleshooting, remediation, and verification.

---

## Lab Environment

### Core Systems

- **SERVER-AD** - Windows Server domain controller
- **FEKRI-WS** - Windows client/workstation
- **fekri.local** - Active Directory lab domain
- **VirtualBox** - Virtualization platform

### Technologies & Tools

- Windows Server
- Windows 11
- Active Directory Domain Services (AD DS)
- DNS
- Group Policy
- PowerShell
- Windows command-line tools
- SMB File Sharing
- NTFS Permissions
- Remote Desktop
- Windows Firewall
- Event Viewer
- Performance troubleshooting tools
- Windows Server Backup / `wbadmin`
- Volume Shadow Copy Service (VSS)

---

## Troubleshooting Methodology

The primary troubleshooting model used throughout the project was:

```text
Scope
  ↓
Triage
  ↓
Evidence Collection
  ↓
Failure Domain
  ↓
Root Cause
  ↓
Minimum Safe Fix
  ↓
Functional Verification
  ↓
Documentation / Escalation
```

The objective was not simply to make a service work again, but to understand **why it failed, what layer was responsible, what evidence supported the diagnosis, and how to prove recovery**.

---

## Project Phases

### Phase 1 - Infrastructure Baseline & Health Assessment

Established the technical baseline of the environment and validated core server, network, Active Directory, DNS, directory-service, and client health.

### Phase 2 - Advanced Active Directory Administration & Troubleshooting

Investigated and resolved Active Directory incidents involving user accounts, disabled accounts, authentication, group membership, authorization, account lockout, and account lifecycle conditions.

### Phase 3 - Advanced DNS & Network Troubleshooting

Performed DNS and network troubleshooting involving client/server connectivity, DNS cache behavior, record validation, name-resolution incidents, and verified recovery.

### Phase 4 - Group Policy Troubleshooting

Investigated Group Policy scope, security filtering, precedence, processing behavior, and policy application using evidence from `gpresult` and related tools.

### Phase 5 - Advanced File Services & Access Control

Worked with SMB shares, NTFS permissions, effective access, authorization failures, permission inheritance, and layered access-control troubleshooting.

### Phase 6 - Client & Remote Support Troubleshooting

Validated remote-support workflows, Remote Desktop connectivity, Windows Firewall behavior, and client-side troubleshooting.

### Phase 7 - Advanced Enterprise Support Tickets

Applied a ticket-oriented troubleshooting process to realistic simulated enterprise incidents without relying on random configuration changes.

### Phase 8 - Security & System Hardening Troubleshooting

Validated system security, administrative access, Windows Firewall behavior, domain secure-channel health, and other hardening-related conditions.

### Phase 9 - Backup, Recovery & Operational Resilience

Implemented and verified a complete file-level recovery lifecycle using Windows Server Backup:

```text
Known Data
  ↓
VSS-Based Backup
  ↓
Remote Backup Repository
  ↓
Recovery Point Verification
  ↓
Controlled Data Loss
  ↓
Actual Recovery
  ↓
Object Verification
  ↓
Content Verification
```

---

## Flagship Troubleshooting & Recovery Cases

### Active Directory Account & Authorization Troubleshooting

The lab included investigation of disabled accounts, account lockout conditions, group membership, and authorization failures.

The troubleshooting process emphasized distinguishing authentication problems from authorization problems before modifying permissions or account configuration.

### DNS Troubleshooting

DNS incidents were investigated by separating:

- Network reachability
- DNS client configuration
- Cache behavior
- DNS records
- Server-side DNS functionality
- Name-resolution verification

This prevented DNS symptoms from automatically being treated as DNS root causes.

### Group Policy Troubleshooting

Group Policy incidents were analyzed using scope, security filtering, precedence, and effective policy results.

```text
Policy Exists
→ Scope
→ Security Filtering
→ Processing
→ Effective Result
→ Minimum Remediation
→ Verification
```

### SMB & NTFS Access Control

File-services incidents were analyzed across multiple layers:

```text
Network Connectivity
→ TCP 445
→ SMB Service
→ Share Availability
→ Authentication
→ Share Permissions
→ NTFS Permissions
→ Effective Access
```

This helped distinguish connectivity, authentication, and authorization failures instead of treating every `Access Denied` condition as the same problem.

### Remote Support & Firewall

Remote connectivity was validated through layered troubleshooting rather than immediately disabling security controls.

```text
Host Reachability
→ Required Port
→ Windows Service
→ Firewall Rules
→ Authentication
→ Functional Remote Access
```

### Backup & Recovery

A dedicated recovery lab was created on `SERVER-AD`.

Test data:

```text
C:\Recovery-Lab\Recovery-Proof.txt
```

Backup repository:

```text
\\FEKRI-WS\Server-Backup
```

A one-time VSS-based backup was created and the recovery version was verified.

The protected file was intentionally removed to simulate controlled data loss.

The file was successfully recovered from the selected backup version, followed by verification that:

- The recovered file existed
- Recovery completed successfully
- The recovered content matched the original known content
- The backup repository remained reachable
- The recovery version remained discoverable

**Core operational lesson:**

> Backup completion is not the same as proven recovery. Recovery must be tested and verified.

---

## Selected Evidence

The repository contains **66 hands-on evidence artifacts** documenting the complete lab.

### Infrastructure Health

- <a href="./evidence/01-Server-Network-Baseline%20.png">Server Network Baseline</a>
- <a href="./evidence/02-dcdiag-health-check%20.png">Domain Controller Health Check</a>
- <a href="./evidence/03-dns-health-check%20.png">DNS Health Check</a>
- <a href="./evidence/04-critical-ad-services%20.png">Critical Active Directory Services</a>
- <a href="./evidence/05-Client-network-baseline%20.png">Client Network Baseline</a>
- <a href="./evidence/06-secure-channel-verification%20.png">Secure Channel Verification</a>

### Active Directory Troubleshooting

- <a href="./evidence/08-ad-user-investigation%20.png">Active Directory User Investigation</a>
- <a href="./evidence/09-ad-account-disabled%20.png">Disabled Account Verification</a>

### Backup & Recovery

- <a href="./evidence/62-backup-recovery-baseline%20.png">Backup and Recovery Baseline</a>
- <a href="./evidence/63-file-backup-success%20.png">File Backup Success</a>
- <a href="./evidence/64-backup-version-verified%20.png">Backup Version Verification</a>
- <a href="./evidence/65-file-recovery-verified%20.png">File Recovery Verification</a>
- <a href="./evidence/66-final-recovery-verification%20.png">Final Recovery Verification</a>

> **Full technical evidence:** Browse the complete `evidence/` directory containing artifacts 01–66.

---

## Skills Demonstrated

### Hands-On Validated

- Windows Server administration
- Active Directory administration
- User and group troubleshooting
- Authentication and authorization troubleshooting
- DNS configuration and troubleshooting
- Network connectivity troubleshooting
- Group Policy troubleshooting
- SMB file sharing
- NTFS permissions
- Effective access analysis
- Remote Desktop troubleshooting
- Windows Firewall troubleshooting
- Windows service troubleshooting
- PowerShell-based diagnostics
- Event-based troubleshooting
- Performance investigation
- Security and system hardening
- Secure-channel validation
- Enterprise-style incident troubleshooting
- Windows Server Backup
- VSS-based backup
- Recovery-point discovery
- Controlled file-loss testing
- File-level recovery
- Post-recovery content verification

---

## Recovery Knowledge Boundaries

The project distinguishes between skills executed hands-on and recovery concepts studied at methodology level.

### Hands-On

- File/folder backup
- Remote backup repository
- Backup-version discovery
- Controlled data loss
- File-level recovery
- Recovery verification

### Methodology / Recovery Awareness

- System State Backup & Recovery
- Windows Recovery Environment (WinRE)
- Bare-Metal / Full-System Recovery

System State and Bare-Metal recovery were intentionally **not destructively executed** against the functioning domain controller.

---

## Key Lessons Learned

1. Troubleshoot the failure domain before changing configuration.
2. A symptom is not automatically the root cause.
3. Authentication and authorization are separate troubleshooting layers.
4. Share permissions and NTFS permissions must be evaluated together.
5. Network reachability does not prove application-layer connectivity.
6. A successful command does not replace functional verification.
7. Security controls should not be disabled as a first troubleshooting step.
8. Use the minimum safe remediation supported by evidence.
9. A backup should not be considered operationally proven until recovery succeeds.
10. Documentation and evidence are part of professional incident closure.

---

## Evidence Philosophy

Evidence in this repository was collected to demonstrate:

```text
Observed Condition
→ Investigation
→ Technical Decision
→ Remediation
→ Verification
```

Screenshots are intended as technical evidence, not as a substitute for understanding the troubleshooting process.

---

## Project Status

```text
Infrastructure Implementation   COMPLETE
Technical Phases                9 / 9 COMPLETE
Hands-On Evidence               66 ARTIFACTS
Troubleshooting Validation      COMPLETE
Backup & Recovery Validation    COMPLETE
Portfolio Documentation         COMPLETE
```

**Status: COMPLETE**

---

## Author

**Fikri Hameed**

IT Support | Windows Server | Active Directory | Troubleshooting | Infrastructure Support

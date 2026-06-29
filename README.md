# Detection Engineering Portfolio

A structured library of production-grade detection content built and maintained by a Cyber Security Threat Detection Engineer working across approximately 80 client tenants in a managed security services environment.

All detections are threat-informed, mapped to the [MITRE ATT&CK framework](https://attack.mitre.org/), and developed from real-world adversary behaviour observed across financial services, government, and commercial environments.

---

## Repository Structure

```
detection-engineering/
│
├── detections/                  # KQL detection rules by MITRE tactic
│   ├── execution/
│   ├── defense-evasion/
│   ├── persistence/
│   ├── credential-access/
│   ├── discovery/
│   ├── command-and-control/
│   └── initial-access/
│
├── sigma/                       # Vendor-agnostic Sigma rules
│   └── (mirrors detections/ tactic structure)
│
├── automation/                  # PowerShell tooling for Sentinel management
│   └── README.md
│
└── README.md
```

---

## Detection Rule Format

Every KQL rule includes a structured YAML metadata header:

```yaml
// ---
// name: <Alert name>
// description: <What the rule detects and why it matters>
// mitre_technique: <Technique ID e.g. T1562.001>
// mitre_tactic: <Tactic e.g. Defense Evasion>
// severity: <Critical | High | Medium | Low>
// data_sources: <e.g. DeviceRegistryEvents, SecurityEvent>
// author: Tarun Wagjiani
// date: <YYYY-MM-DD>
// ---
```

---

## Coverage

| Tactic | Examples |
|---|---|
| Defense Evasion | AMSI bypass via registry, BYOVD, EDR tampering |
| Execution | LOLBin abuse, ClickFix WebDAV delivery, RunMRU execution |
| Credential Access | RC4 Kerberos downgrade, OAuth abuse, MFA registration anomalies |
| Persistence | Azure role assignment abuse, Conditional Access exclusions |
| Command and Control | Netsh port forwarding, RMM tool abuse (ScreenConnect) |
| Initial Access | ISO and container file delivery chains, PsExec lateral movement |
| Discovery | USB device enumeration, GitHub audit log anomalies |

---

## Automation

The `automation/` folder contains PowerShell scripts for managing Microsoft Sentinel deployments at scale across multi-tenant MSSP environments via Azure Lighthouse and GDAP:

- Bulk analytics rule management (create, update, delete) across tenants
- Severity and tactic updates across rule libraries
- Threat indicator ingestion via the Microsoft Defender for Endpoint API
- Cross-tenant workspace discovery and reporting

Each script includes inline documentation covering purpose, required permissions, and example usage. All environment-specific values have been replaced with placeholder variables.

---

## Sigma Rules

The `sigma/` folder contains vendor-agnostic versions of selected detections written in [Sigma format](https://github.com/SigmaHQ/sigma), enabling translation to Splunk ES, Google SecOps, Elastic, and other SIEM platforms via the [pySigma](https://github.com/SigmaHQ/pySigma) toolchain.

---

## Methodology

Detection content in this repository follows a structured development lifecycle:

1. **Identify** — source technique from threat intelligence, incident findings, or ATT&CK coverage gap analysis
2. **Research** — understand how the technique presents across relevant log sources and artefacts
3. **Build** — develop detection logic with appropriate filtering to minimise false positives
4. **Validate** — test against real or simulated telemetry; document expected true and false positive profile
5. **Document** — add YAML metadata, triage guidance, and MITRE mapping before committing

---

## Tools and Platforms

- **SIEM** — Microsoft Sentinel, Microsoft Defender XDR
- **Query language** — KQL (Kusto Query Language)
- **Detection format** — KQL (native), Sigma (vendor-agnostic)
- **Automation** — PowerShell, Azure Logic Apps, Azure CLI
- **CI/CD** — GitHub Actions (YAML metadata validation on push)
- **Framework** — MITRE ATT&CK

---

## Contact

**Tarun Wagjiani** — Cyber Security Detection Engineer  
[linkedin.com/in/tarun-wagjiani-69397818a](https://www.linkedin.com/in/tarun-wagjiani-69397818a)  
[github.com/tarun24000](https://github.com/tarun24000)

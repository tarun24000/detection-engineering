# Detection Engineering Portfolio

A structured library of production grade detection content built and maintained by CSA's Cyber Security Threat Detection Engineer working across approximately 80 client Sentinel tenants.

---
## Repository Structure

```
detection-engineering/
│
├── detections/                  
│   ├── execution/
│   ├── defense-evasion/
│   ├── persistence/
│   ├── credential-access/
│   ├── discovery/
│   ├── command-and-control/
│   └── initial-access/
│
├── sigma/                       
│   └── (mirrors detections/ tactic structure)
│
├── useful-automation-scripts/                  
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
| Credential Access | OAuth abuse, MFA registration anomalies |
| Persistence | Azure role assignment abuse, Conditional Access exclusions |
| Command and Control | Netsh port forwarding, RMM tool abuse (ScreenConnect) |
| Initial Access | ISO and container file delivery chains, PsExec lateral movement |
| Discovery | USB device enumeration, GitHub audit log anomalies |

---



Each script includes inline documentation covering purpose, required permissions, and example usage. All environment-specific values have been replaced with placeholder variables.

---

## Sigma Rules

The `sigma/` folder contains vendor-agnostic versions of selected detections written in [Sigma format](https://github.com/SigmaHQ/sigma), enabling translation to Splunk ES, Google SecOps, Elastic, and other SIEM platforms via the [pySigma](https://github.com/SigmaHQ/pySigma) toolchain.

## Tools and Platforms

- **SIEM** — Microsoft Sentinel, Microsoft Defender XDR
- **Query language** — KQL (Kusto Query Language)
- **Detection format** — KQL (native), Sigma
- **Automation** — PowerShell, Azure Logic Apps, Azure CLI
- **CI/CD** — GitHub Actions (YAML metadata validation on push)
- **Framework** — MITRE ATT&CK

---

## Contact

**Tarun Wagjiani** — Cyber Security Detection Engineer  
[linkedin.com/in/tarun-wagjiani-69397818a](https://www.linkedin.com/in/tarun-wagjiani-69397818a)  
[github.com/tarun24000](https://github.com/tarun24000)

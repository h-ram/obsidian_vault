**EDR** is a system designed to **detect, investigate, and respond to threats on endpoints** (such as computers, servers, and mobile devices) in real-time. It provides **continuous monitoring, threat detection, and automated response** to security incidents.

---
### **How EDR Works**
1. **Data Collection** – Captures logs, system activities, and network connections from endpoints.
2. **Threat Detection** – Uses AI, heuristics, and known attack patterns to identify threats.
3. **Automated Response** – Isolates affected devices, stops malicious processes, and removes threats.
4. **Forensic Analysis** – Provides detailed insights into attack vectors and root causes.
---
### **Popular EDR Solutions**
- **CrowdStrike Falcon** – AI-driven, cloud-based EDR.
- **Microsoft Defender for Endpoint** – Integrates with Windows security tools.
- **SentinelOne** – Automated detection and response with rollback capability.
- **Carbon Black (VMware)** – Behavioral-based threat detection.
- **Sophos Intercept X** – Advanced anti-ransomware and AI-driven analysis.
---
### **EDR vs. [[Security information and event management (SIEM)|SIEM]]**

Both **EDR** and **SIEM** are cybersecurity solutions, but they serve different purposes and have different scopes.

| Feature                    | **EDR (Endpoint Detection & Response)**                                                           | **SIEM (Security Information & Event Management)**                                              |
| -------------------------- | ------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| **Focus**                  | Protects **endpoints** (PCs, servers, workstations).                                              | Monitors **entire IT infrastructure** (networks, endpoints, servers, applications).             |
| **Data Source**            | Collects data from **individual endpoints**.                                                      | Collects logs from **multiple sources** (firewalls, IDS/IPS, endpoints, cloud, etc.).           |
| **Threat Detection**       | Uses **behavioral analysis, heuristics, and AI** to detect **malware, ransomware, and exploits**. | Uses **log correlation and rule-based analysis** to detect **network-wide security incidents**. |
| **Response Capabilities**  | Can **automatically respond** (quarantine devices, kill processes, block threats).                | Mainly **alerts security teams** but does not take direct action.                               |
| **Incident Investigation** | Provides **detailed forensic data** about endpoint activities.                                    | Helps security teams **analyze attack patterns** across an organization.                        |
| **Use Case**               | Protecting **endpoints from targeted attacks**.                                                   | **Aggregating and analyzing** security events across the IT environment.                        |
| **Automation**             | Uses AI and **automated threat response**.                                                        | Uses **correlation rules and SIEM playbooks**, but response is often manual.                    |
| **Example Tools**          | CrowdStrike Falcon, Microsoft Defender for Endpoint, SentinelOne, Carbon Black.                   | Splunk, IBM QRadar, ArcSight, Graylog.                                                          |

---
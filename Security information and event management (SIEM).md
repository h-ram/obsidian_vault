**SIEM** is a system that **collects, analyzes, and correlates** security data from across The organization's IT infrastructure. It helps **detect, investigate, and respond** to security threats in real time.

---
### **How SIEM Works**
1. **Data Collection** – Logs from various sources (firewalls, antivirus, applications, network devices) are collected.
2. **Normalization** – Data is structured in a common format for analysis.
3. **Correlation** – Events are linked to detect security incidents.
4. **Alerting & Response** – Alerts are generated, and security teams respond to threats.
---
### **Common SIEM Tools**
- **Splunk** – Advanced threat detection with real-time monitoring.
- **IBM QRadar** – AI-powered analytics for detecting sophisticated attacks.
- **ArcSight (Micro Focus)** – Scalable SIEM with advanced correlation features.
- **LogRhythm** – Automates threat detection and response.
- **AlienVault (AT&T Cybersecurity)** – Includes SIEM + IDS + vulnerability management.
---
### **SIEM vs. [[Endpoint Detection and Response (EDR)|EDR]]**

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
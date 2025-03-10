**PCAP (Packet Capture)** is a file format used to store network traffic captured by tools like **Wireshark, TShark, tcpdump, and Zeek**. It contains raw network packets, including **headers, payloads, timestamps, and metadata**, allowing for later analysis and forensic investigation.

---
## **PCAP File Formats**
There are different variations of PCAP formats:
1. **PCAP (Classic Format)** – `.pcap`
    - Standard format used by Wireshark and tcpdump.
2. **PCAP-NG (Next Generation)** – `.pcapng`
    - Supports **multiple interfaces, metadata, and better compression**.
3. **PCAP-over-IP (Remote Capture)**
    - Used for capturing traffic remotely via `rpcapd`.
---
## **Tools for Capturing PCAP Files**
### **a) Wireshark (GUI & CLI via TShark)**
```sh
tshark -i eth0 -w capture.pcap
```
- Captures packets on **eth0** and saves them to **capture.pcap**.
### **b) tcpdump (CLI, Lightweight Alternative)**
```sh
tcpdump -i eth0 -w traffic.pcap
```
- Captures packets on **eth0** and writes them to **traffic.pcap**.
### **c) Zeek (Network Security Monitoring)**
```sh
zeek -r capture.pcap
```
- Analyzes **PCAP files** for security insights.
---
## **4. How to Read PCAP Files**
### **a) Using Wireshark (GUI)**
- Open **Wireshark**, click **File > Open**, and select the `.pcap` file.
- Use filters to inspect specific traffic (e.g., `http.request` to see HTTP requests).
### **b) Using TShark (CLI)**
```sh
tshark -r capture.pcap
```
- Reads **PCAP files** in the terminal.
### **c) Extract Specific Traffic from PCAP**
```sh
tshark -r capture.pcap -Y "tcp.port == 443"
```
- Filters **HTTPS (port 443) traffic** from the file.
---
## **5. PCAP File Extraction & Analysis**
### **a) Extract HTTP Requests**

```sh
tshark -r traffic.pcap -Y "http.request" -T fields -e http.host
```
- Extracts **HTTP hosts** from captured traffic.
### **b) Extract Passwords (if unencrypted)**
```sh
tshark -r traffic.pcap -Y "ftp.request.command == USER || ftp.request.command == PASS"
```
- Finds **FTP credentials** (useful for security analysis).
### **c) Convert PCAP to Text (JSON, CSV, XML)**
```sh
tshark -r capture.pcap -T json > output.json
```
- Converts the PCAP file to **JSON format**.
---
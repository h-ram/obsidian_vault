#networking 

An [[Internet Protocol address (IP address)|IP Address]] has multiple Ports that are used to manage where each traffic is handled (e.g web connections with http are in port 80)
* The [[Internet Protocol address (IP address)|IP Address]] is the building.
* The ports are the individual apartments in that building. The mail is sent to your building first (IP address), and then the building manager (operating system) distributes the mail to the appropriate apartment (port).
---
### How many Ports are there?
There are 65,536 network ports in total, numbered from 0 to 65,535. (because a port is represented in 16 bits, i.e 2^16 = 65,536)
### Port Categories
- **Well-Known Ports (0–1023)**: Reserved for system or widely-used protocols like HTTP (80), HTTPS (443), FTP (21), and others.
- **Registered Ports (1024–49151)**: Used for applications or services that are not as standardized but still require well-known ports.
- **Dynamic/Private Ports (49152–65535)**: Used by client-side applications for temporary or private connections, often assigned dynamically by the operating system.
### TCP vs UDP Ports
Some Ports are connection oriented and care more about every packet arriving, so they're used by [[Transmission Control Protocol (TCP)|TCP]]. While other Ports are connectionless and care about speed more, so they're used by [[User Datagram Protocol (UDP)|UPD]]. And some ports can be used by [[Transmission Control Protocol (TCP)|TCP]] or [[User Datagram Protocol (UDP)|UDP]]
### Common Ports
| Port(s)   | Transport Protocol | Service Name/Protocol | Description                                                                  |
| --------- | ------------------ | --------------------- | ---------------------------------------------------------------------------- |
| `20`/`21` | (TCP)              | `FTP`                 |                                                                              |
| `22`      | (TCP)              | `SSH`                 | Secure Shell, secure logins, file transfers (scp, sftp), and port forwarding |
| `23`      | (TCP)              | `Telnet`              |                                                                              |
| `25`      | (TCP)              | `SMTP`                |                                                                              |
| `80`      | (TCP)              | `HTTP`                |                                                                              |
| `161`     | (TCP/UDP)          | `SNMP`                |                                                                              |
| `389`     | (TCP/UDP)          | `LDAP`                |                                                                              |
| `443`     | (TCP)              | `SSL`/`TLS` (`HTTPS`) |                                                                              |
| `445`     | (TCP)              | `SMB`                 |                                                                              |
| `3389`    | (TCP)              | `RDP`                 |                                                                              |
![[common-ports.pdf]]
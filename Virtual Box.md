A TYPE-2 [[Hypervisor]]

---
# Network
| Network Mode         | Communication                 | External Access**        | **Use Case**                         |
| -------------------- | ----------------------------- | ------------------------ | ------------------------------------ |
| **NAT**              | VM ↔ Host ↔ External          | Yes (via Host)           | Internet access, isolated VM         |
| **Bridged**          | VM ↔ Host ↔ LAN (External)    | Yes (direct access)      | Full network access, server testing  |
| **Internal Network** | VM ↔ VM (within same network) | No                       | Isolated network, testing lab setup  |
| **Host-Only**        | VM ↔ Host                     | No                       | Local communication with Host only   |
| **NAT Network**      | VM ↔ VM ↔ Host ↔ External     | Yes (via Host)           | Multi-VM communication with internet |
| **Generic Driver**   | Custom communication          | Depends on configuration | Special network requirements         |
### 1. **NAT (Network Address Translation)**
- **Purpose**: Allows VMs to access external networks (e.g., the internet) but prevents external systems from initiating connections to the VM.
- **How It Works**:
    - The VM is assigned a private IP address within the VirtualBox network.
    - VirtualBox acts as a gateway, using NAT to translate the private IP address to the host machine's public IP address when the VM communicates with external networks.
    - Incoming connections from the outside world are blocked unless configured otherwise (e.g., port forwarding).
- **Use Case**: Ideal for scenarios where the VM needs internet access but does not require external systems to connect to it directly (e.g., browsing the web, updates, or package installations).
### 2. **Bridged Adapter**
- **Purpose**: Connects the VM directly to the physical network, allowing it to act as if it is another physical machine on the network.
- **How It Works**:
    - The VM gets an IP address from the same DHCP server as the host machine or is assigned a static IP address within the same subnet.
    - The VM can communicate with any device on the physical network (same subnet).
- **Use Case**: Ideal when you want the VM to be fully accessible from other devices on the network (e.g., running a server that needs to be accessed by other machines on the same network).
### 3. **Internal Network**
- **Purpose**: Allows communication between VMs that are attached to the same internal network but isolates them from the outside world.
- **How It Works**:
    - VMs connected to the same internal network can communicate with each other, but they cannot access the host machine or external networks.
    - This creates a "private network" between the VMs.
- **Use Case**: Used for scenarios like testing or penetration testing where you want VMs to communicate in an isolated environment (e.g., lab testing, multi-VM environments).
### 4. **Host-Only Adapter**
- **Purpose**: Allows communication between the VM and the host machine, but isolates the VM from the external network.
- **How It Works**:
    - The VM is assigned an IP address within a virtual network range that can only be accessed by the host machine and other VMs connected to the same host-only network.
    - No communication to the external network (such as the internet) is possible, but communication between the host and VM is allowed.
- **Use Case**: Useful for setups where the VM needs to interact with the host for file sharing, testing, or managing a local service but does not need external internet access.
### 5. **NAT Network**
- **Purpose**: Similar to NAT, but with the ability to allow multiple VMs on the same network to communicate with each other and with the external world.
- **How It Works**:
    - VMs are connected to a shared network created by VirtualBox, and they are able to communicate with each other using private IPs.
    - These VMs can access the internet using the host machine's IP, and they also can interact with each other within the NAT network.
- **Use Case**: Ideal for scenarios where you want VMs to communicate with each other and the internet without exposing the VMs directly to the external network (e.g., multi-VM testing environments with external access).
### 6. **Generic Driver**
- **Purpose**: Provides the ability to use custom network drivers, such as for virtual machines using special or specialized network configurations.
- **How It Works**:
    - Allows users to configure the network interfaces in a way that’s not available with the standard adapters.
- **Use Case**: Typically used for more advanced or specific network configurations that aren't covered by the other options.


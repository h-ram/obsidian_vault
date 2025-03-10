A **hypervisor** is software that creates and manages **virtual machines (VMs)** by allocating system resources such as CPU, memory, and storage. It allows multiple operating systems to run on a single physical machine while keeping them isolated from each other.
### Types of Hypervisor
1. **TYPE-1 Hypervisor:** (bare metal hypervisor, Native Hypervisor)
	- Runs **directly on the hardware** without a host OS.
	- More efficient and secure, mainly used in **enterprise environments**.
	- **Examples**: VMware ESXi, Microsoft Hyper-V, Xen.
2. **TYPE-2 Hypervisor:** (Hosted Hypervisor)
	- Runs **on top of a host OS**, like an application.
	- Easier to use but less efficient than Type 1.
	- **Examples**: VirtualBox, VMware Workstation, Parallels.
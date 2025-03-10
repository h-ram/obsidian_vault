#cloud 

Amazon **EC2 (Elastic Compute Cloud)** is an [[Amazon Web Services (AWS)|AWS]] service that lets you rent **virtual computers (servers)** in the cloud. Instead of buying and maintaining physical servers, you can quickly create, use, and scale virtual machines as needed.

---
# **How EC2 Works?**
1. **Launch an EC2 Instance**
    - Select an **Amazon Machine Image (AMI)** (OS template).
    - Choose an **instance type** (CPU, RAM, network performance).
    - Configure storage (EBS or Instance Store).
    - Assign a security group (firewall rules).
    - Choose a **key pair** (SSH authentication).
	- Start Instant
2. **Connect to the EC2 Instance**
    - For **Linux**, use SSH:
        ```bash
        ssh -i my-key.pem ec2-user@<EC2-IP>
        ```
    - For **Windows**, use RDP or [[PuTTY]]
3. **Run Applications** → Host websites, databases, or apps.
4. **Scale Up or Down** → Add or remove servers based on demand.
    - Use **Elastic Load Balancer (ELB)** to distribute traffic.
    - Set up **Auto Scaling** to adjust capacity dynamically.
---
# **EC2 Pricing Options**
- **On-Demand** → Pay for what you use (flexible).
- **Reserved** → Pay upfront for lower cost (long-term).
- **Spot Instances** → Get unused servers at a discount (cheaper but can be interrupted).
# **Key Features of EC2**
1. **Elasticity & Scalability**
    - You can **increase or decrease** the number of virtual machines based on demand.
    - Supports **Auto Scaling Groups (ASG)** for automatic scaling.
2. **Multiple Instance Types**
    - EC2 offers different **instance types** optimized for compute, memory, storage, or GPU workloads.
    - **Examples:**
        - **General Purpose** – (e.g., `t3`, `m5` instances) for balanced workloads.
        - **Compute Optimized** – (e.g., `c5` instances) for CPU-heavy applications.
        - **Memory Optimized** – (e.g., `r5`, `x1e` instances) for in-memory databases.
        - **Storage Optimized** – (e.g., `i3`, `d2` instances) for large disk-intensive workloads.
        - **GPU Instances** – (e.g., `p4`, `g5` instances) for machine learning and graphics processing.
3. **Choice of Operating Systems**
    - Supports multiple OS: **Linux (Ubuntu, RHEL, CentOS, Amazon Linux)** and **Windows Server**.
4. **Flexible Pricing Models**
    - **On-Demand Instances** – Pay per hour or second, no long-term commitment.
    - **Reserved Instances (RI)** – Commit to 1 or 3 years for lower pricing.
    - **Spot Instances** – Up to **90% cheaper** than On-Demand, but can be interrupted.
    - **Savings Plans** – Flexible discount pricing based on usage patterns.
    - **Dedicated Hosts** – Physical server dedicated to a single organization.
5. **Storage Options**
    - **Elastic Block Store (EBS)** – Persistent storage volumes for EC2.
    - **Instance Store (Ephemeral Storage)** – Temporary storage tied to the instance lifecycle.
    - **Amazon EFS** – Scalable file storage for shared workloads.
    - **Amazon S3** – Object storage for backups and data storage.
6. **Security & Networking**
    - **VPC (Virtual Private Cloud)** – Isolated networking environment for EC2 instances.
    - **Security Groups & NACLs** – Firewalls to control inbound/outbound traffic.
    - **IAM Roles** – Secure access control for EC2 instances.
7. **Load Balancing & High Availability**
    - **Elastic Load Balancer (ELB)** distributes traffic across multiple instances.
    - **Auto Scaling Groups (ASG)** automatically adjust capacity.
    - **Multi-Region & Multi-AZ Deployment** ensures redundancy.
---
# **EC2 Use Cases**
- **Web Hosting** – Deploy websites & web applications.
- **Big Data Processing** – Run analytics & machine learning models.
- **High-Performance Computing (HPC)** – Scientific computing & simulations.
- **Development & Testing** – CI/CD pipelines & test environments.
- **Enterprise Applications** – SAP, databases, and enterprise workloads.

---
# **EC2 Alternatives in Other Cloud Providers**
- **Microsoft Azure** – Azure Virtual Machines (VMs).
- **Google Cloud Platform (GCP)** – Google Compute Engine (GCE).
- **IBM Cloud** – IBM Virtual Servers.
- **Oracle Cloud** – Oracle Compute Instances.
Amazon EC2 is the **core compute service** in AWS, offering flexibility, scalability, and security for running cloud applications.
---
# **Etymology**
The "2" in EC2 is there because two words start with C (Compute Cloud).
```
Elastic Compute Cloud -> ECC -> EC2
```
- **Elastic** → You can increase or decrease the number of servers anytime.
- **Compute** → Provides computing power (CPU, RAM, etc.).
- **Cloud** → Runs on AWS, so no physical hardware is needed.




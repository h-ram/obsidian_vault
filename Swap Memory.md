Swap is a space on your Hard drive (hdd or ssd) used as **virtual memory** when RAM is full. It helps prevent system crashes by temporarily moving less-used data from RAM to disk.
## Types of Swap:
1. **Swap Partition** – A dedicated partition on the disk.
2. **Swap File** – A file on an existing filesystem, more flexible.
## When to Use Swap:
- If your system has **low RAM** (<4GB).
- Running **heavy applications** (e.g., video editing, VMs).
- On **servers** to prevent out-of-memory errors.
## When to Avoid Swap:
- If you have **plenty of RAM** (>16GB) and no heavy workloads.
- On SSDs (reduces wear, but can still be used).

## Etymology
It's called **swap** because it "swaps" data between RAM and disk storage. When RAM is full, the system moves (or **swaps out**) less-used memory pages to disk (swap space). When needed again, those pages are **swapped back** into RAM.

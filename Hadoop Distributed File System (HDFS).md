**HDFS**  is the primary **storage layer** in the Hadoop ecosystem. It is designed to **store and manage large datasets** across multiple machines in a **fault-tolerant, scalable, and distributed** manner.

---
# **Key Features of HDFS**
1. **Distributed Storage**: Splits large files into smaller blocks and distributes them across multiple nodes.
2. **Fault Tolerance**: Replicates data blocks across different nodes to prevent data loss.
3. **High Throughput**: Optimized for large sequential read/write operations.
4. **Scalability**: Can handle petabytes of data by adding more nodes.
5. **Write Once, Read Many (WORM)**: Designed for batch processing where files are written once and read multiple times.
6. **Commodity Hardware**: Works on low-cost machines without requiring high-end storage.
---
# **HDFS Architecture**
HDFS follows a **Master-Slave Architecture** with three main components:
1.  **NameNode (Master)**
	- Manages metadata and the namespace of HDFS (e.g., file locations, replication).
	- Keeps track of which DataNodes store which blocks.
	- Does not store actual data.
2. **DataNodes (Slaves)**
	- Store the actual data blocks.
	- Perform read and write operations upon instruction from the NameNode.
	- Periodically send a **heartbeat** signal to the NameNode to confirm they are active.
3. **Secondary NameNode**
	- Not a backup of the NameNode.
	- Helps in **checkpointing** the metadata and merging the edits log to optimize performance.
	- Prevents the NameNode from becoming overloaded.
---
# **HDFS File Storage Mechanism**
4. A file is **split into fixed-size blocks** (default: **128 MB or 256 MB**).
5. Each block is **replicated (default: 3 copies) on different DataNodes** for fault tolerance.
6. The **NameNode maintains metadata** (block locations, file permissions, etc.).
7. Clients interact with the **NameNode to retrieve metadata** and then communicate directly with **DataNodes to read/write data**.

**Example:**
- Suppose you store a 500MB file in HDFS.
- If the block size is 128MB, the file will be split into 4 blocks:
    - Block 1: 128MB
    - Block 2: 128MB
    - Block 3: 128MB
    - Block 4: 116MB
- Each block is stored on **three different DataNodes**.
---
# **HDFS Commands**
### **5.1 Basic Commands**
```bash
# List files and directories in HDFS root.
hdfs dfs -ls /

# Create a new directory in HDFS.
hdfs dfs -mkdir /user/data

# Upload a file from local to HDFS.
hdfs dfs -put localfile.txt /user/data/

# Download a file from HDFS to local.
hdfs dfs -get /user/data/file.txt localfile.txt

# Delete a file from HDFS.
hdfs dfs -rm /user/data/file.txt

# Remove an empty directory.
hdfs dfs -rmdir /user/data

# Show disk usage of HDFS files/directories.
hdfs dfs -du -h /user/
```
### **5.2 File Operations**

```bash
# Create a directory in HDFS
hdfs dfs -mkdir /data

# Upload a file from local to HDFS
hdfs dfs -put sample.txt /data/

# View the contents of a file
hdfs dfs -cat /data/sample.txt

# Copy a file within HDFS
hdfs dfs -cp /data/sample.txt /backup/sample_copy.txt

# Move a file within HDFS
hdfs dfs -mv /data/sample.txt /backup/

# Download a file from HDFS to local
hdfs dfs -get /backup/sample.txt ./sample_local.txt
```

### **5.3 HDFS Permissions & Ownership**

```bash
# Change file ownership in HDFS
hdfs dfs -chown user:group /data/sample.txt

# Change file permissions in HDFS
hdfs dfs -chmod 755 /data/sample.txt
```

### **5.4 Block Replication & Health Check**

```bash
# Check file block locations and replication factor
hdfs fsck /data/sample.txt -files -blocks -locations

# Set replication factor to 2 for a file
hdfs dfs -setrep 2 /data/sample.txt
```

---
# **HDFS High Availability (HA)**
HDFS supports **high availability (HA)** to prevent single points of failure:
1. **Active & Standby NameNode**:
    - One **Active NameNode** handles operations.
    - One **Standby NameNode** acts as a backup in case of failure.
2. **JournalNodes**:
    - Synchronizes metadata between Active and Standby NameNodes.
    - Ensures consistent state between NameNodes.

---
# **Data Processing on HDFS**
- **Hadoop MapReduce**: Batch processing of large datasets stored in HDFS.
- **Apache Spark**: In-memory data processing using HDFS.
- **Apache Hive**: SQL-based querying on HDFS data.
- **Apache HBase**: NoSQL database running on HDFS for real-time read/write access.

---
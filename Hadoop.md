Apache Hadoop is an open-source framework designed for storing and processing [[Big Data]] across distributed clusters of computers. Hadoop is a framework, and its components are:
- [[Hadoop Distributed File System (HDFS)]] 
- [[Yet Another Resource Negotiator (YARN)]]
- [[Hadoop MapReduce]]
# **Installation**
-  **Install Java and ssh**
```bash
sudo apt update
sudo apt install openjdk-17-jdk ssh -y
java -version
```
- **Download Hadoop** Find the latest version of hadoop [here](https://hadoop.apache.org/releases.html) , ours is 3.4.1
```bash
# Replace 3.4.1 with the latest version 
wget https://downloads.apache.org/hadoop/common/hadoop-3.4.1/hadoop-3.4.1.tar.gz
```
-  **Extract Hadoop Archive**
```bash
tar -xzvf hadoop-3.4.1.tar.gz
sudo mv hadoop-3.4.1 /usr/local/hadoop
rm hadoop-3.4.1.tar.gz
```
- **Set Up SSH**
 Now check that you can ssh to the localhost without a passphrase:
```bash
  ssh localhost
```
If you cannot ssh to localhost without a passphrase, execute the following commands:
```bash
  ssh-keygen -t rsa -P '' -f ~/.ssh/id_rsa
  cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys
  chmod 0600 ~/.ssh/authorized_keys
```
- **Set Up Environment Variables**
```bash
vim $HADOOP_HOME/etc/hadoop/hadoop-env.sh
JAVA_HOME=/usr/lib/jvm/java-17-openjdk-amd64
```

```bash
vim ~/.bashrc
export JAVA_HOME=/usr/lib/jvm/java-17-openjdk-amd64
export HADOOP_HOME=/usr/local/hadoop
export HADOOP_INSTALL=$HADOOP_HOME
export HADOOP_CONF_DIR=$HADOOP_HOME/etc/hadoop

export PATH=$PATH:JAVA_HOME/bin
export PATH=$PATH:$HADOOP_HOME/bin  
export PATH=$PATH:$HADOOP_HOME/sbin

export HADOOP_MAPRED_HOME=$HADOOP_HOME  
export YARN_HOME=$HADOOP_HOME  
export HADOOP_COMMON_LIB_NATIVE_DIR=$HADOOP_HOME/lib/native  
export HADOOP_OPTS="-Djava.library.path=$HADOOP_HOME/lib/native"  
export HADOOP_STREAMING=$HADOOP_HOME/share/hadoop/tools/lib/hadoop-streaming-3.4.1.jar
export HADOOP_LOG_DIR=$HADOOP_HOME/logs  
export PDSH_RCMD_TYPE=ssh

source ~/.bashrc
```
-  **Configure Hadoop**
	Edit the core configuration file:
	```bash
	vim $HADOOP_HOME/etc/hadoop/core-site.xml
	```
	Add the following configuration:
	```xml
	<configuration>
	    <property>
	        <name>fs.defaultFS</name>
	        <value>hdfs://localhost:9000</value>
	    </property>
	</configuration>
	```
	Edit the HDFS configuration file:
	```bash
	vim $HADOOP_HOME/etc/hadoop/hdfs-site.xml
	```
	Add the following configuration:
	```xml
	<configuration>
	    <property>
	        <name>dfs.replication</name>
	        <value>1</value>
	    </property>
	</configuration>
	```
- **Format the Hadoop Filesystem**
Before starting Hadoop, format the HDFS filesystem:
```bash
hdfs namenode -format
```
- **Start Hadoop Services**
Now start the HDFS and YARN:
```bash
start-dfs.sh
start-yarn.sh
```
OR you can start both of them with:
```bash
start-all.sh
```

> [!warning] Notice
> You must start hadoop daemons (HDFS and YARN) everytime you reboot your system

You can stop hadoop with these commands:
```bash
stop-dfs.sh
stop-yarn.sh
# OR
stop-all.sh
```
- **Check Hadoop Status**
To check if the Hadoop services are running, use:
```bash
$ jps
4881 NameNode
5190 SecondaryNameNode
4983 DataNode
6511 Jps
```
You should see processes like `NameNode`, `DataNode`, `ResourceManager`, and `NodeManager`.
- **Access Hadoop Web UI**
	- **HDFS Web UI**: `http://localhost:9870/`
	- **YARN Web UI**: `http://localhost:8088/`
- **Test Hadoop**
You can run a simple test like creating directories or running a sample MapReduce job:
```bash
hdfs dfs -mkdir /user/yourusername
hdfs dfs -put input.txt /user/yourusername
```
---
Resrouces:
- https://hadoop.apache.org/docs/stable/hadoop-project-dist/hadoop-common/SingleCluster.html
---
# **Etymology**
The name **Hadoop** comes from the creator **Doug Cutting**'s son's **toy elephant**. Doug Cutting was the co-founder of the Apache Hadoop project, and when he was looking for a name, his son’s stuffed elephant, named _Hadoop_, inspired him. According to Doug, the name doesn't have a particular meaning beyond the association with the toy elephant.
The name stuck and became iconic in the world of big data, symbolizing the project's ability to handle large datasets in a distributed manner, much like an elephant can carry heavy loads.

---
Resources:
- https://www.youtube.com/watch?v=1vbXmCrkT3Y&ab_channel=edureka%21
- https://www.youtube.com/watch?v=pqT4AgPuzZ0&list=PL6UwySlcwEYJ2hFuGIvr4VEHUAfl-GCNT&ab_channel=AmpCode
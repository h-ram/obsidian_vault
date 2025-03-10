
# **Installation**

### Step 1: Prerequisites
Before installing Spark, ensure your system has the necessary dependencies.
#### 1.1 Install Java
Spark requires Java (versions 8, 11, or 17 are supported). We'll install OpenJDK 11 here.
   ```bash
   sudo apt update
   sudo apt install openjdk-11-jdk -y
   java -version
   # openjdk version "11.0.21" 2023-10-17
   ```
#### 1.2 Install Python
Spark works with Python 3.6+. Most Linux distributions come with Python pre-installed, but let's ensure you have it.
   ```bash
   sudo apt install python3 python3-pip -y
   python3 --version
   pip3 --version
   ```
---
### Step 2: Download and Install Apache Spark
We'll download the latest version of Spark from the official website and set it up.
1. Visit the [Apache Spark Downloads page](https://spark.apache.org/downloads.html) to check for the latest version and get the download link
2. use `wget` to download Spark with Hadoop support (you can choose "without Hadoop" if you don't need it).
   ```bash
	wget https://downloads.apache.org/spark/spark-3.5.0/spark-3.5.0-bin-hadoop3.tgz
   ```
3. Extract the tarball:
	```bash
   tar -xzf spark-3.5.0-bin-hadoop3.tgz
   ```
4. Move it to a system-wide directory (e.g., `/opt/spark`):
   ```bash
   sudo mv spark-3.5.0-bin-hadoop3 /opt/spark
   ```
#### 2.3 Set Environment Variables
To make Spark accessible from anywhere, set environment variables.
1. Open your shell configuration file (e.g., `~/.bashrc` or `~/.zshrc`):
   ```bash
   nano ~/.bashrc
   ```
2. Add the following lines at the end:
   ```bash
   export SPARK_HOME=/opt/spark
   export PATH=$PATH:$SPARK_HOME/bin:$SPARK_HOME/sbin
   export PYSPARK_PYTHON=python3
   ```
3. Reload the configuration:
   ```bash
   source ~/.bashrc
   ```
4. Verify Spark is accessible:
   ```bash
   spark-shell --version
   ```
   If installed correctly, this should display the Spark version.

---

### Step 3: Install PySpark
PySpark is the Python API for Spark. You can install it via `pip` to simplify Python integration.

1. Install PySpark using pip (ensure the version matches your Spark installation):
   ```bash
   pip3 install pyspark==3.5.0
   ```
   This installs PySpark and its dependencies.
2. Verify PySpark installation:
   ```bash
   pyspark --version
   ```
   It should match your Spark version.

---

### Step 4: Configure Spark (Optional Tweaks)
Spark works out of the box for most local setups, but you can tweak configurations for better performance.

#### 4.1 Memory Settings
Edit `$SPARK_HOME/conf/spark-defaults.conf` (create it if it doesn't exist):
1. Copy the template:
   ```bash
   cp $SPARK_HOME/conf/spark-defaults.conf.template $SPARK_HOME/conf/spark-defaults.conf
   ```
2. Edit the file:
   ```bash
   nano $SPARK_HOME/conf/spark-defaults.conf
   ```
3. Add or modify these lines to set memory limits:
   ```
   spark.driver.memory 4g
   spark.executor.memory 2g
   ```
   Adjust based on your system's RAM.

#### 4.2 Logging
Spark can be verbose. To reduce log noise:
1. Copy the log4j properties template:
   ```bash
   cp $SPARK_HOME/conf/log4j2.properties.template $SPARK_HOME/conf/log4j2.properties
   ```
2. Edit the file:
   ```bash
   nano $SPARK_HOME/conf/log4j2.properties
   ```
3. Change the log level from `INFO` to `WARN` or `ERROR`:
   ```
   rootLogger.level=WARN
   ```

---

### Step 5: Test Apache Spark with Python
Now let's write a simple PySpark script to ensure everything works.

#### 5.1 Create a Python Script
1. Create a file called `test_spark.py`:
   ```bash
   nano test_spark.py
   ```
2. Add the following code:
   ```python
   from pyspark.sql import SparkSession

   # Create a Spark session
   spark = SparkSession.builder \
       .appName("SimpleTest") \
       .getOrCreate()

   # Create a sample DataFrame
   data = [("Alice", 25), ("Bob", 30), ("Charlie", 35)]
   columns = ["Name", "Age"]
   df = spark.createDataFrame(data, columns)

   # Perform a simple operation
   df.show()

   # Filter and show data
   df_filtered = df.filter(df.Age > 30)
   df_filtered.show()

   # Stop the Spark session
   spark.stop()
   ```
3. Save and exit (`Ctrl+O`, `Enter`, `Ctrl+X`).

#### 5.2 Run the Script
You can run the script in two ways:
- **Directly with Python**:
  ```bash
  python3 test_spark.py
  ```
- **Using `spark-submit`** (recommended for Spark jobs):
  ```bash
  spark-submit test_spark.py
  ```

#### 5.3 Expected Output
If everything is set up correctly, you should see:
```
+-------+---+
|   Name|Age|
+-------+---+
|  Alice| 25|
|    Bob| 30|
|Charlie| 35|
+-------+---+

+-------+---+
|   Name|Age|
+-------+---+
|Charlie| 35|
+-------+---+
```

---

### Step 6: Optional - Set Up a Development Environment
For interactive development, you might prefer using Jupyter Notebook or an IDE.

#### 6.1 Jupyter Notebook Setup
1. Install Jupyter:
   ```bash
   pip3 install jupyter
   ```
2. Install `findspark` to help Jupyter locate Spark:
   ```bash
   pip3 install findspark
   ```
3. Start Jupyter Notebook:
   ```bash
   jupyter notebook
   ```
4. In a notebook cell, initialize Spark:
   ```python
   import findspark
   findspark.init()

   from pyspark.sql import SparkSession
   spark = SparkSession.builder.appName("JupyterTest").getOrCreate()

   # Test with a simple DataFrame
   spark.createDataFrame([("Test", 1)]).show()
   ```

#### 6.2 IDE Setup (e.g., VS Code)
- Install VS Code and the Python extension.
- Set the Python interpreter to your system's Python 3 (where PySpark is installed).
- Use the same script as above (`test_spark.py`) to run and debug.

---

### Step 7: Troubleshooting Common Issues
- **Java Version Mismatch**: If Spark complains about Java, ensure the correct version (e.g., 11) is installed and set in `JAVA_HOME`:
  ```bash
  export JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64
  ```
- **PySpark Not Found**: Ensure PySpark matches your Spark version (`pip install pyspark==3.5.0`).
- **Memory Issues**: If Spark crashes with memory errors, adjust memory settings in `spark-defaults.conf` or reduce the dataset size for testing.

---

### Step 8: Additional Notes
- **Hardware**: For local development, ensure you have at least 8GB of RAM. Spark is memory-intensive.
- **Cluster Setup**: For distributed workloads, you'd need to set up a cluster (e.g., using Spark's standalone mode, YARN, or Kubernetes), but the above setup works for local mode.
- **Updates**: Check the Spark website periodically for newer versions and adjust the download URL accordingly.

---

### Summary
You've now installed Apache Spark (latest version as of this guide), configured it, and tested it with Python. You can run Spark jobs using `spark-submit` or interactively via Jupyter Notebook. If you hit any errors or want to dive deeper into a specific use case (like Spark SQL, MLlib, or streaming), let me know! What kind of project are you planning with Spark?
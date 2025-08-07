# Apache Spark Local Setup

## Table of Contents
- [1. Installing Spark Locally (Native Installation)](#1-installing-spark-locally-native-installation)
  - [1.1 Prerequisites](#11-prerequisites)
  - [1.2 Download and Install Spark](#12-download-and-install-spark)
  - [1.3 Set Environment Variables](#13-set-environment-variables)
  - [1.4 Install Required Python Libraries](#14-install-required-python-libraries)
  - [1.5 Test Your Installation](#15-test-your-installation)
- [2. Using Docker to Set Up Spark](#2-using-docker-to-set-up-spark)
  - [2.1 Prerequisites](#21-prerequisites)
  - [2.2 Standalone Setup](#22-standalone-setup)
  - [2.3 Set Up Spark Cluster](#23-set-up-spark-cluster)
    - [2.3.1 Start the Cluster](#231-start-the-cluster)
    - [2.3.2 Access the Spark Web UI](#232-access-the-spark-web-ui)
    - [2.3.3 Submit Jobs](#233-submit-jobs)
    - [2.3.4 Setting Up Jupyter Notebook Container for Spark (Optional)](#234-setting-up-jupyter-notebook-container-for-spark-optional)
    - [2.3.5 Test Notebook Code](#235-test-notebook-code)

---

In this section, we'll cover two common ways to set up Apache Spark on a local development machine:

1. **Installing Spark Locally (Native Installation)**
2. **Using Docker to Set Up Spark**

---

## 1. Installing Spark Locally (Native Installation)

This method involves manually installing Spark and its dependencies on your machine.

### 1.1 Prerequisites

- **Java (JDK 8 or 11):** Spark runs on the JVM.
- **Python 3.x:** Required for PySpark.

### 1.2 Download and Install Spark

- Download Spark from the [Official Apache Spark website](https://spark.apache.org/downloads.html).
    - Choose a version (e.g., Spark 3.4.1) and a pre-built package for Hadoop (e.g., "Pre-built for Apache Hadoop 3.3 and later").

#### Extract the archive to a directory of your choice

- **On Linux:**
    ```bash
    tar -xzf spark-3.4.1-bin-hadoop3.tgz -C /path/to/your/directory
    ```
- **On Windows:**
    - Use a tool like 7-Zip or WinRAR.
    - Right-click the downloaded `.tgz` file
    - Select "Extract Here" or "Extract to spark-3.4.1-bin-hadoop3"
    - Move the extracted folder to your desired location

### 1.3 Set Environment Variables

Set the following environment variables so your system can find Spark and Java.

- **Linux (add to `~/.bashrc` or `~/.zshrc`):**
    ```bash
    export SPARK_HOME=/path/to/your/directory/spark-3.4.1-bin-hadoop3
    export PATH=$PATH:$SPARK_HOME/bin
    export JAVA_HOME=/path/to/your/java
    ```
- **Windows:**  
  Set environment variables via System Properties > Environment Variables.

### 1.4 Install Required Python Libraries

```bash
pip install pyspark findspark
```

### 1.5 Test Your Installation

- Start the PySpark shell:
    ```bash
    pyspark
    ```
- Or test with a small script (`main.py`):
    ```python
    import findspark
    findspark.init()

    from pyspark.sql import SparkSession
    spark = SparkSession.builder.appName("Test").getOrCreate()
    print(spark.range(5).collect())
    ```

---

## 2. Using Docker to Set Up Spark

An alternative way is to run Spark inside Docker containers. This avoids manual setup and ensures a clean environment.

### 2.1 Prerequisites

- Docker installed on your system ([Install Docker](https://docs.docker.com/get-docker/))

### 2.2 Standalone Setup

#### 2.2.1 Pull a Spark Docker image

You can use an existing image from Docker Hub or customize it using a Dockerfile.

```bash
docker pull bitnami/spark
```

#### 2.2.2 Run a Spark Container

Start a Spark standalone container:

```bash
docker run -it bitnami/spark pyspark
```

### 2.3 Set Up Spark Cluster

You can create a local Spark cluster with [`docker-compose.yaml`](./docker-compose.yaml).

#### 2.3.1 Start the Cluster

Run the following command to start the cluster:

```bash
docker compose up -d
```

#### 2.3.2 Access the Spark Web UI

- Master: [http://localhost:8080](http://localhost:8080)
- Worker: [http://localhost:8081](http://localhost:8081)

#### 2.3.3 Submit Jobs

You can submit jobs using the spark-submit tool or run a PySpark shell inside the container:

```bash
docker exec -it spark-master pyspark --master spark://spark-master:7077
```

#### 2.3.4 Setting Up Jupyter Notebook Container for Spark (Optional)

Running a Jupyter Notebook container alongside your Spark services is a great way to interactively test Spark code using PySpark.

- Uncomment the `jupyter` service block in the [`docker-compose.yaml`](./docker-compose.yaml) file.
- Ensure the `notebooks` directory exists in the same location as your `docker-compose.yaml`:
    ```bash
    mkdir notebooks
    ```
  This directory will be mounted into the Jupyter container so that your notebooks are saved persistently.

- To start the whole cluster (including Jupyter):
    ```bash
    docker-compose up -d
    ```
- To start only the Jupyter container (after cluster is running):
    ```bash
    docker-compose up -d jupyter
    ```
- You can now access the notebook UI at: [http://localhost:8888](http://localhost:8888)

  Use the token shown in the terminal (when the Jupyter container starts) to log in.

#### 2.3.5 Test Notebook Code

In a new notebook, run:

```python
from pyspark.sql import SparkSession

spark = SparkSession.builder \
    .appName("NotebookSpark") \
    .master("spark://spark-master:7077") \
    .getOrCreate()

spark.range(5).show()
```
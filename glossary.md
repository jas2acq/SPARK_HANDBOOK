# Glossary

### Apache Spark {#apache-spark}
Apache Spark is an open-source distributed analytics engine designed for large-scale data processing and machine learning. It is widely recognized for its ability to perform fast, in-memory computations and can scale effortlessly from a single machine to vast clusters. Spark provides APIs in several popular programming languages including Python (via PySpark), Scala, Java, and R, making it accessible for diverse data tasks.

### Big Data {#big-data}
Big Data refers to datasets that are so large, complex, or rapidly generated that traditional data processing systems cannot handle them efficiently. These datasets are typically characterized by the three Vs—high Volume, high Velocity, and high Variety—demanding specialized frameworks like Spark for effective storage, processing, and analysis.

### Distributed Data Processing Framework {#distributed-data-processing-framework}
A distributed data processing framework is a software system that facilitates the division of data and computational workloads across multiple machines or nodes in a cluster. This arrangement enables parallelism, fault tolerance, and scalability, which are critical for handling big data workloads efficiently, as exemplified by Apache Spark.

### Distributed Analytics Engine {#distributed-analytics-engine}
A distributed analytics engine is a software system designed to process and analyze large datasets across multiple machines or nodes in a cluster, enabling scalable and parallel computation for data analytics workloads.

### Machine Learning {#machine-learning}
Machine learning is a subset of artificial intelligence that enables systems to automatically learn and improve from experience without being explicitly programmed, often used for predictive analytics and pattern recognition in large datasets.

### Master-Slave Architecture {#master-slave-architecture}
This architecture defines a system design where a central master node, known as the driver in Spark, controls and coordinates the execution of application tasks. Multiple slave or worker nodes, known as executors, perform actual data computations upon instruction from the master. This master-slave setup is fundamental to Spark's ability to distribute computation.

### Driver {#driver}
The driver is the primary process and master program in a Spark application, responsible for orchestrating execution across the cluster. It initializes the SparkContext, translates user code into an optimized logical execution plan represented as a Directed Acyclic Graph (DAG), breaks down the application into jobs, stages, and tasks, schedules these tasks on executors, and handles fault tolerance by managing retries and resource allocation.

### Logical Execution Plan {#logical-execution-plan}
A logical execution plan is an abstract representation of the computation flow that describes what operations need to be performed on the data, before being converted into a physical execution plan for actual execution.

### Jobs {#jobs}
Jobs are units of work triggered by actions in Spark applications. Each job corresponds to one action and consists of multiple stages that are executed to produce the final result.

### SparkContext {#sparkcontext}
SparkContext is the main entry point to interact with Spark's cluster, providing the interface for your application to communicate with the cluster manager. It manages distributed data structures like RDDs, handles broadcast variables and accumulators, and coordinates the execution of tasks by acting as the gateway to Spark's core functionalities.

### Accumulators {#accumulators}
Accumulators are shared variables that can be efficiently updated by multiple tasks in parallel, typically used for counters or sums across distributed computations.

### Broadcast Variables {#broadcast-variables}
Broadcast variables are read-only variables cached on each machine rather than shipping a copy of it with tasks, useful for efficiently distributing large datasets to all nodes.

### Executors {#executors}
Executors are distributed worker processes launched by the cluster manager on individual nodes within the cluster. They execute tasks assigned by the driver, store intermediate computation results in memory or disk, perform caching of data to enhance performance, and communicate their task completion status back to the driver. Executors remain active for the full duration of the Spark application they serve.

### Cluster Manager {#cluster-manager}
The cluster manager is a resource management component responsible for allocating CPU cores, memory, and other resources to Spark applications within a cluster. It launches the driver and executor processes as requested, monitors node health, manages resource contention, and handles failure scenarios to ensure smooth distributed execution. Spark supports multiple cluster managers including Standalone, Apache Mesos, Hadoop YARN, and Kubernetes.

### Standalone Cluster Manager {#standalone-cluster-manager}
The standalone cluster manager is Spark's built-in cluster manager that provides a simple way to set up and manage Spark clusters without requiring external resource management systems.

### Apache Mesos {#apache-mesos}
Apache Mesos is a general-purpose cluster manager that can efficiently share resources among distributed applications and frameworks, including Spark.

### Hadoop YARN {#hadoop-yarn}
Hadoop YARN (Yet Another Resource Negotiator) is a resource management platform responsible for managing compute resources in Hadoop clusters and scheduling applications.

### Kubernetes {#kubernetes}
Kubernetes is an open-source container orchestration platform that automates the deployment, scaling, and management of containerized applications, including Spark applications.

### Distributed Collections {#distributed-collections}
Distributed collections are data structures partitioned and spread across multiple nodes in a cluster enabling parallel processing. The cornerstone of Spark's data abstractions is the Resilient Distributed Dataset (RDD), which embodies this concept by organizing immutable datasets distributed across the cluster.

### Distributed Datasets {#distributed-datasets}
Distributed datasets are collections of data that are partitioned and stored across multiple machines in a cluster, enabling parallel processing and fault tolerance.

### Distributed Processing {#distributed-processing}
Distributed processing is the method of dividing computational tasks across multiple machines or processors to achieve parallel execution and handle large-scale workloads efficiently.

### Resilient Distributed Dataset (RDD) {#resilient-distributed-dataset-rdd}
RDDs are immutable, distributed collections of data that can be processed in parallel across the nodes of a cluster. They support two fundamental operation types: transformations, which are lazy and build new RDDs, and actions, which trigger computation and return results. Their fault tolerance comes from lineage information that records the sequence of transformations so Spark can recompute lost partitions after failures.

### RDDs {#rdds}
See [Resilient Distributed Dataset (RDD)](#resilient-distributed-dataset-rdd).

### Lineage Information {#lineage-information}
Lineage information is metadata that Spark maintains to track the sequence of transformations applied on RDDs. This record allows Spark to efficiently recover lost data partitions by replaying transformations when nodes fail, thereby enabling fault tolerance without replicating the data physically.

### Transformations {#transformations}
Transformations are lazy, functional operations applied to RDDs that define a new RDD without immediately executing any computation. Common examples include `map`, `filter`, and `flatMap`. They enable the construction of a DAG representing a processing pipeline, which Spark optimizes before executing.

### Actions {#actions}
Actions are operations on RDDs or DataFrames that trigger the actual execution of the data processing pipeline, returning results to the driver or saving outputs externally. Examples of actions are `collect`, `count`, and `reduce`. These operations finalize a Spark job by activating the transformations defined earlier.

### Directed Acyclic Graph (DAG) {#directed-acyclic-graph-dag}
The Directed Acyclic Graph (DAG) in Spark represents the logical flow of transformations as a graph with directed edges and no cycles. It models the sequence and dependencies of operations and is used by Spark's DAG Scheduler to optimize and break down jobs into executable stages, improving the efficiency of distributed computations.

### DAG Scheduler {#dag-scheduler}
The DAG Scheduler is a Spark component responsible for converting the high-level DAG created from user transformations into stages composed of tasks. It groups these tasks based on their data dependencies and shuffle boundaries, organizing execution in a manner that minimizes costly data shuffles and maximizes parallelism.

### Stages {#stages}
Stages are subdivisions within a Spark job formed by the DAG Scheduler. Each stage represents a set of tasks that can be executed in parallel without requiring data shuffling. Stages are separated by shuffle boundaries and are the primary units of scheduling and execution in Spark.

### Tasks {#tasks}
Tasks are the smallest units of work in Spark. Each task corresponds to an executable job on a single partition of data and is assigned by the task scheduler to executors. Parallel execution of tasks across the cluster nodes enables the scalability and speed of Spark.

### Task Scheduler {#task-scheduler}
The task scheduler is the Spark component that assigns individual tasks within stages to executors, taking into account data locality, available resources, and cluster state to ensure efficient execution and load balancing.

### Shuffle Boundaries {#shuffle-boundaries}
Shuffle boundaries represent points in the computation when data must be redistributed across the cluster via network communication, such as after `groupBy` or `join` operations. These boundaries demarcate stage divisions in Spark's execution DAG, as shuffles require data to be exchanged between executors.

### In-Memory Computation {#in-memory-computation}
In-memory computation is Spark's approach to enhance performance by processing data directly in RAM rather than relying on slower disk-based storage. This technique significantly speeds up iterative algorithms and interactive analytics by reducing I/O overhead.

### Data Caching {#data-caching}
Data caching involves persisting a dataset, such as an RDD or DataFrame, in memory across operations to avoid recomputation or repeated disk reads. This optimization is particularly beneficial for algorithms or workflows that reuse the same data multiple times.

### Fault Tolerance {#fault-tolerance}
Fault tolerance is Spark's ability to detect, handle, and recover from failures during distributed processing by leveraging lineage information to recompute lost or corrupted partitions without replicating data unnecessarily. This resilience ensures reliability in large-scale deployments.

### Job Scheduling {#job-scheduling}
Job scheduling is the process by which Spark organizes, prioritizes, and dispatches units of work (jobs), which are initiated by actions, across the cluster to executors. Scheduling manages dependencies, resource allocation, and execution order to optimize throughput.

### Fault Recovery {#fault-recovery}
Fault recovery involves mechanisms that restart failed tasks and reassign work to healthy executors, while fault handling encompasses detection of failures, retries, and resource reallocation to maintain job continuity and robustness in Spark applications.

### Fault Handling {#fault-handling}
See [Fault Recovery](#fault-recovery).

### Pipeline Execution {#pipeline-execution}
Pipeline execution or stage pipelining describes the ability to chain multiple transformations within the same stage without incurring shuffle costs. This approach reduces disk I/O by performing a sequence of operations in a single pass over the data inside an executor.

### Stage Pipelining {#stage-pipelining}
See [Pipeline Execution](#pipeline-execution).

### Driver Execution Modes {#driver-execution-modes}
Spark supports multiple driver execution modes influencing where the driver runs relative to the cluster: in **cluster mode**, the driver executes on a cluster worker node; in **client mode**, it runs on the client machine submitting the job; and in **local mode**, both driver and executors run locally on one machine for development and testing.

### Spark Core {#spark-core}
Spark Core is the foundational module providing essential functionalities such as the RDD API, task scheduling, memory management, and fault tolerance. It underpins all Spark workloads and is critical for job execution orchestration.

### Spark SQL {#spark-sql}
Spark SQL is a Spark module that enables processing structured and semi-structured data using familiar SQL syntax and a DataFrame API. It supports querying via standard SQL, Hive QL, and integrates native optimizations through the Catalyst optimizer, accommodating various sources such as Parquet and JSON.

### DataFrames {#dataframes}
DataFrames are distributed data collections organized into named columns with a schema, offering a higher-level abstraction than RDDs. They provide optimized query execution, a user-friendly API similar to SQL tables or pandas DataFrames, and facilitate integration with Spark SQL.

### MLlib {#mllib}
MLlib is Spark's scalable machine learning library providing distributed implementations of common algorithms like classification, regression, clustering, and collaborative filtering. It also offers utilities for feature extraction, transformation, and evaluation in large-scale workloads.

### Spark Streaming {#spark-streaming}
Spark Streaming extends Spark's capabilities to process real-time data streams by breaking continuous data into micro-batches. It supports fault-tolerant stream processing and integrates with sources like Kafka to enable near real-time analytics.

### GraphX {#graphx}
GraphX is a Spark library specializing in processing graphs and graph-parallel computations. It enables users to perform graph analytics and manipulate graph-structured data distributedly, efficiently combining graph and data-parallel computations.

### Kafka {#kafka}
Kafka is a distributed publish-subscribe messaging system frequently used as a high-throughput data source for Spark Streaming. It reliably ingests and buffers data streams for processing in real time.

### Cluster Mode {#cluster-mode}
Cluster mode is a Spark execution mode where the driver runs inside the cluster on one of the worker nodes. The cluster manager manages both the driver and all executor processes, making it suitable for production deployments where the driver needs to be resilient and managed by the cluster infrastructure.

### Client Mode {#client-mode}
Client mode is a Spark execution mode where the driver runs on the client machine from which the job was submitted, while executors run on the cluster nodes. This mode is useful for interactive debugging, testing, and development scenarios where direct communication with the driver is needed.

### Local Mode {#local-mode}
Local mode is a Spark execution mode where the entire Spark application executes on a single machine using multiple threads for parallelism. This mode is primarily used for development, experimentation, and debugging purposes and is not recommended for production workloads due to limited scalability.
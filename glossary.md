# Glossary

- **[Apache Spark](https://spark.apache.org/)**: An open-source, distributed data processing framework designed for handling big data workloads with speed, ease of use, and flexibility.

- **[big data](https://en.wikipedia.org/wiki/Big_data)**: Large and complex datasets that traditional data processing tools cannot handle efficiently, often characterized by volume, velocity, and variety.

- **[distributed data processing framework](https://en.wikipedia.org/wiki/Distributed_computing)**: A system that processes data across multiple nodes in a cluster to achieve parallelism and scalability.

- **[master-slave architecture](https://en.wikipedia.org/wiki/Master/slave_(technology))**: A model where one central node (master) coordinates and delegates tasks to multiple worker nodes (slaves).

- **[driver](https://spark.apache.org/docs/latest/cluster-overview.html#components)**: The central coordinator of a Spark application, responsible for running the main program, creating the SparkContext, and managing job execution.

- **[SparkContext](https://spark.apache.org/docs/latest/api/python/reference/api/pyspark.SparkContext.html)**: The entry point to Spark functionalities, acting as the interface between the Spark application and the cluster.

- **[logical execution plan](https://spark.apache.org/docs/latest/sql-execution-plan.html)**: A high-level representation of the computations to be performed, created by the driver from the user’s code.

- **[jobs](https://spark.apache.org/docs/latest/job-scheduling.html)**: High-level units of work in Spark, triggered by actions in the user’s code.

- **[stages](https://spark.apache.org/docs/latest/job-scheduling.html#stage-boundaries)**: Subdivisions of a job, created by the DAG Scheduler, grouping tasks that can be executed together without requiring a shuffle.

- **[tasks](https://spark.apache.org/docs/latest/job-scheduling.html#task-scheduling)**: The smallest unit of work in Spark, executed by executors on individual data partitions.

- **[executors](https://spark.apache.org/docs/latest/cluster-overview.html#components)**: Worker processes running on cluster nodes that execute tasks, store data, and communicate results back to the driver.

- **[fault tolerance](https://spark.apache.org/docs/latest/rdd-programming-guide.html#fault-tolerance)**: The ability of Spark to recover from failures by recomputing lost data using lineage information.

- **[cluster manager](https://spark.apache.org/docs/latest/cluster-overview.html#cluster-manager)**: A system that allocates and manages resources across a cluster for Spark applications.

- **[distributed collections](https://spark.apache.org/docs/latest/rdd-programming-guide.html#resilient-distributed-datasets-rdds)**: Data structures like RDDs that are partitioned across multiple nodes in a cluster for parallel processing.

- **[RDDs](https://spark.apache.org/docs/latest/rdd-programming-guide.html#resilient-distributed-datasets-rdds)**: Resilient Distributed Datasets, immutable collections of objects partitioned across a cluster, providing fault tolerance and parallel processing.

- **[accumulators](https://spark.apache.org/docs/latest/rdd-programming-guide.html#accumulators)**: Variables that allow aggregation of information across executors, typically used for counters or sums.

- **[broadcast variables](https://spark.apache.org/docs/latest/rdd-programming-guide.html#broadcast-variables)**: Read-only variables cached on each node to reduce data transfer overhead during task execution.

- **[standalone cluster manager](https://spark.apache.org/docs/latest/spark-standalone.html)**: Spark’s built-in cluster manager for simple cluster setups.

- **[Apache Mesos](http://mesos.apache.org/)**: A general-purpose cluster manager that supports multiple frameworks, including Spark.

- **[Hadoop YARN](https://hadoop.apache.org/docs/current/hadoop-yarn/hadoop-yarn-site/YARN.html)**: A resource manager used in Hadoop ecosystems, compatible with Spark for resource allocation.

- **[Kubernetes](https://kubernetes.io/)**: A container orchestration platform that can manage Spark applications in a containerized environment.

- **[Directed Acyclic Graph (DAG)](https://spark.apache.org/docs/latest/job-scheduling.html#dag-scheduler)**: A graph representing the sequence of computations in Spark, with no cycles, used to optimize execution.

- **[transformations](https://spark.apache.org/docs/latest/rdd-programming-guide.html#transformations)**: Lazy operations on RDDs that define a new RDD without immediately computing it (e.g., map, filter).

- **[actions](https://spark.apache.org/docs/latest/rdd-programming-guide.html#actions)**: Operations that trigger computation on RDDs and return results to the driver (e.g., collect, count).

- **[DAG Scheduler](https://spark.apache.org/docs/latest/job-scheduling.html#dag-scheduler)**: A component that divides the DAG into stages based on shuffle boundaries and data dependencies.

- **[Task Scheduler](https://spark.apache.org/docs/latest/job-scheduling.html#task-scheduler)**: A component that assigns tasks to executors for execution.

- **[shuffle boundaries](https://spark.apache.org/docs/latest/rdd-programming-guide.html#shuffle-operations)**: Points in the computation where data needs to be redistributed across nodes, separating stages.

- **[in-memory computation](https://spark.apache.org/docs/latest/rdd-programming-guide.html#in-memory-computation)**: Spark’s approach to processing data in memory to minimize disk I/O and improve performance.

- **[data caching](https://spark.apache.org/docs/latest/rdd-programming-guide.html#caching)**: Storing frequently used datasets in memory to speed up iterative or repeated computations.

- **[machine learning](https://spark.apache.org/docs/latest/ml-guide.html)**: A field of data processing involving algorithms that learn from data, supported by Spark’s MLlib.

- **[stage pipelining](https://spark.apache.org/docs/latest/job-scheduling.html#pipelining)**: Combining multiple operations within a stage to avoid unnecessary disk writes, improving efficiency.

- **[lineage information](https://spark.apache.org/docs/latest/rdd-programming-guide.html#fault-tolerance)**: Metadata about RDD transformations, used to recompute lost data partitions for fault tolerance.

- **[Spark Core](https://spark.apache.org/docs/latest/)**: The foundational layer of Spark, handling job scheduling, memory management, fault recovery, and task dispatching.

- **[Spark SQL](https://spark.apache.org/docs/latest/sql-programming-guide.html)**: A module for structured data processing, supporting SQL and Hive Query Language.

- **[Spark Streaming](https://spark.apache.org/docs/latest/streaming-programming-guide.html)**: A module for real-time data processing using micro-batch streaming.

- **[MLlib](https://spark.apache.org/docs/latest/ml-guide.html)**: Spark’s machine learning library, offering scalable algorithms for classification, regression, clustering, and more.

- **[GraphX](https://spark.apache.org/docs/latest/graphx-programming-guide.html)**: A module for graph processing and computation on distributed datasets.

- **[Kafka](https://kafka.apache.org/)**: A distributed streaming platform often used as a data source for Spark Streaming.

- **[distributed datasets](https://spark.apache.org/docs/latest/rdd-programming-guide.html#resilient-distributed-datasets-rdds)**: Collections of data partitioned across a cluster for parallel processing, such as RDDs.

- **[distributed processing](https://spark.apache.org/docs/latest/)**: The execution of computations across multiple nodes in a cluster to handle large-scale data.

- **[job scheduling](https://spark.apache.org/docs/latest/job-scheduling.html)**: The process of organizing and prioritizing jobs for execution in Spark.

- **[fault recovery](https://spark.apache.org/docs/latest/rdd-programming-guide.html#fault-tolerance)**: The mechanism by which Spark recovers from failures using lineage information.

- **[fault handling](https://spark.apache.org/docs/latest/rdd-programming-guide.html#fault-tolerance)**: The process of managing and mitigating failures in Spark, including task retries and resource reallocation.

- **[pipeline execution](https://spark.apache.org/docs/latest/job-scheduling.html#pipelining)**: The execution of multiple operations in a single stage without requiring data shuffling.
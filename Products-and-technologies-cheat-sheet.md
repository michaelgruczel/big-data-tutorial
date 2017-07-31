# Products and technologies cheat sheet

## hadoop

Apache Hadoop is an open source framework for distributed storage and processing of large sets of data on commodity hardware.
The base Apache Hadoop framework is composed of the following modules:

* Hadoop Common – contains libraries and utilities needed by other Hadoop modules.
* Hadoop Distributed File System (HDFS) – a distributed file-system that stores data on commodity machines, providing very high aggregate bandwidth across the cluster.
* Hadoop YARN – a resource-management platform responsible for managing computing resources in clusters and using them for scheduling of users’ applications.
* Hadoop MapReduce – a programming model for large scale data processing.

**Data Management**

Store and process vast quantities of data in a storage layer that scales linearly:

* Apache Hadoop YARN
* HDFS– Hadoop Distributed File System (HDFS) is a Java-based file system that provides scalable and reliable data.
It was designed to span large clusters of commodity servers. HDFS has demonstrated production scalability of up to 200 PB of storage and a single cluster of 4500 servers, supporting close to a billion files and blocks. 

**Data Access**

Interact with your data in a wide variety of ways – from batch to real-time:

* Apache Hive – Built on the MapReduce framework, Hive is a data warehouse that enables easy data summarization and ad-hoc queries via an SQL-like interface for large datasets stored in HDFS.
* Apache Pig – A platform for processing and analyzing large data sets.
* MapReduce – MapReduce is a framework for writing applications that process large amounts of structured and unstructured data in parallel across a cluster of thousands of machines, in a reliable and fault-tolerant manner.
* Apache Spark – Spark is ideal for in-memory data processing. It allows data scientists to implement fast, iterative algorithms for advanced analytics such as clustering and classification of datasets.
* Apache Storm – Storm is a distributed real-time computation system for processing fast, large streams of data adding reliable real-time data processing capabilities to Apache Hadoop® 2.x
* Apache HBase – A column-oriented NoSQL data storage system that provides random real-time read/write access to big data for user applications.
* Apache Tez – Tez generalizes the MapReduce paradigm to a more powerful framework for executing a complex DAG (directed acyclic graph) of tasks for near real-time big data processing.
* Apache Kafka – Kafka is a fast and scalable publish-subscribe messaging system that is often used in place of traditional message brokers because of its higher throughput, replication, and fault tolerance.
* Apache HCatalog – A table and metadata management service that provides a centralized way for data processing systems to understand the structure and location of the data stored within Apache Hadoop.
* Apache Slider – A framework for deployment of long-running data access applications in Hadoop. Slider leverages YARN’s resource management capabilities to deploy those applications, to manage their lifecycles and scale them up or down.
* Apache Solr– Solr is the open source platform for searches of data stored in Hadoop. Solr enables powerful full-text search and near real-time indexing on many of the world’s largest Internet sites.
* Apache Mahout – Mahout provides scalable machine learning algorithms for Hadoop which aids with data science for clustering, classification and batch based collaborative filtering.
* Apache Accumulo – Accumulo is a high performance data storage and retrieval system with cell-level access control. It is a scalable implementation of Google’s Big Table design that works on top of Apache Hadoop and Apache ZooKeeper.

**Data Governance and Integration**

Quickly and easily load data, and manage according to polic:

* Apache Falcon – Falcon is a data management framework for simplifying data lifecycle management and processing pipelines on Apache Hadoop®. It enables users to orchestrate data motion, pipeline processing,disaster recovery, and data retention workflows.
* Apache Flume – Flume allows you to efficiently aggregate and move large amounts of log data from many different sources to Hadoop.
* Apache Sqoop – Sqoop is a tool that speeds and eases movement of data in and out of Hadoop. It provides a reliable parallel load for various, popular enterprise data sources.

**Security**

Address requirements of Authentication, Authorization, Accounting and Data Protection:

* Apache Knox – The Knox Gateway (“Knox”) provides a single point of authentication and access for Apache Hadoop services in a cluste
* Apache Ranger – Apache Ranger delivers a comprehensive approach to security for a Hadoop cluster. It provides central security policy administration across the core enterprise security requirements of authorization, accounting and data protection

**Operations**

Provision, manage, monitor and operate Hadoop clusters at scale:

* Apache Ambari – An open source installation lifecycle management, administration and monitoring system for Apache Hadoop clusters.
* Apache Oozie – Oozie Java Web application used to schedule Apache Hadoop jobs. Oozie combines multiple jobs sequentially into one logical unit of wor
* Apache ZooKeeper – A highly available system for coordinating distributed processes. Distributed applications use ZooKeeper to store and mediate updates to important configuration information.

## Hortonworks Data Platform (HDP)

Hortonworks Data Platform (HDP) is a packaged software Hadoop distribution that aims to ease deployment and management of Hadoop clusters. Compared with simply downloading the various Apache code bases and trying to run them together a system, HDP greatly simplifies the use of Hadoop. Architected, developed, and built completely in the open, HDP provides an enterprise ready data platform that enables organizations to adopt a Modern Data Architecture.

## HDFS

An HDFS cluster is comprised of a NameNode, which manages the cluster metadata, and DataNodes that store the data. Files and directories are represented on the NameNode by inodes. Inodes record attributes like permissions, modification and access times, or namespace and disk space quotas.
The Namenode actively monitors the number of replicas of a block. When a replica of a block is lost due to a DataNode failure or disk failure, the NameNode creates another replica of the block.

## Ambari

Ambari:

* Ambari Files User View provides a user friendly interface to upload, store and move data. Underlying all components in Hadoop is the Hadoop Distributed File System
* Hive User View provides an interactive interface to Hive.   We can create, edit, save and run queries, and have Hive evaluate them for us using a series of MapReduce jobs or Tez jobs.

## MapReduce

MapReduce is the key algorithm that the Hadoop data processing engine uses to distribute work around a cluster. A MapReduce job splits a large data set into independent chunks and organizes them into key, value pairs for parallel processing.
MapReduce System is composed of the JobTracker, which is the master, and the per-node slaves called TaskTrackers. The JobTracker is responsible for resource management (managing the worker nodes i.e. TaskTrackers), tracking resource consumption/availability and also job life-cycle management (scheduling individual tasks of the job, tracking progress, providing fault-tolerance for tasks etc).
The philosophy of the cluster design is to bring the computing to the data. So each datanode will hold part of the overall data and be able to process the data that it holds


## YARN

Apache YARN (Yet Another Resource Negotiator)

The fundamental idea of YARN is to split up the two major responsibilities of the JobTracker i.e. resource management and job scheduling/monitoring, into separate daemons: a global ResourceManager and per-application ApplicationMaster (AM).
The ResourceManager and per-node slave, the NodeManager (NM -> CPU, memory, disk, network), form the new, and generic, system for managing applications in a distributed manner.
YARN is the architectural center of Hadoop that allows multiple data processing engines such as interactive SQL, real-time streaming, data science and batch processing to handle data stored in a single platform, unlocking an entirely new approach to analytics.
Yarn is a middle layer between the HDFS and the different tools on top of it (Pig, Hive, Spark, ...).

## Apache Hive

Hive is an SQL like query language (Hive QL) that enables those analysts familiar with SQL to run queries on large volumes of data.  Hive has three main functions: data summarization, query and analysis. Hive provides tools that enable easy data extraction, transformation and loading (ETL)
Hive users have a choice of 3 runtimes when executing SQL queries. Users can choose between Apache Hadoop MapReduce, Apache Tez or Apache Spark frameworks as their execution backend.
Hive on LLAP (Live Long and Process) makes use of persistent query servers with intelligent in-memory caching to avoid Hadoop’s batch-oriented latency and provide as fast as sub-second query response times against smaller data volumes, while Hive on Tez continues to provide excellent batch query performance against petabyte-scale data sets.

Parts of it are:

* HCatalog is a component of Hive. It is a table and storage management layer for Hadoop that enables users with different data processing tools — including Pig and MapReduce — to more easily read and write data on the grid.
* WebHCat provides a service that you can use to run Hadoop MapReduce (or YARN), Pig, Hive jobs or perform Hive metadata operations using an HTTP (REST style) interface

## Apache Tez

Apache Tez is an extensible framework for building high performance batch and interactive data processing applications, coordinated by YARN in Apache Hadoop. Tez improves the MapReduce paradigm by dramatically improving its speed, while maintaining MapReduce’s ability to scale to petabytes of data.
Apache Tez provides a developer API and framework to write native YARN applications that bridge the spectrum of interactive and batch workloads. 
Since Tez is extensible and embeddable, it provides the fit-to-purpose freedom to express highly optimized data processing applications, giving them an advantage over end-user-facing engines such as MapReduce and Apache Spark. 

## Apache Pig

Apache Pig allows Apache Hadoop users to write complex MapReduce transformations using a simple scripting language called Pig Latin. Pig translates the Pig Latin script into MapReduce so that it can be executed within YARN for access to a single dataset stored in the Hadoop Distributed File System (HDFS).

## Greenplum

links:

* http://greenplum.org/
* https://pivotal.io/pivotal-greenplum

## Greenplum

Pivotal Greenplum Database is a massively parallel processing (MPP) database server (several PostgreSQL database instances acting together as one cohesive database management system) with an architecture specially designed to manage large-scale analytic data warehouses and business intelligence workloads.
MPP (also known as a shared nothing architecture) refers to systems with two or more processors that cooperate to carry out an operation, each processor with its own memory, operating system and disks.

Greenplum Master

The Greenplum Database master is the entry to the Greenplum Database system, accepting client connections and SQL queries, and distributing work to the segment instances.
The master is where the global system catalog resides. The global system catalog is the set of system tables that contain metadata about the Greenplum Database system itself. The master does not contain any user data; data resides only on the segments. 

Greenplum Segments

Greenplum Database segment instances are independent PostgreSQL databases that each store a portion of the data and perform the majority of query processing.
When a user connects to the database via the Greenplum master and issues a query, processes are created in each segment database to handle the work of that query.

## HAWQ

http://hawq.incubator.apache.org/

HAWQ is “HAdoop With Query” and is basically a port of Greenplum to store data natively in HDFS. This empowers everyone using Hadoop to use a friendlier and more robust programming interface to Hadoop.
There are many “small” features in Greenplum Database that either aren’t supported yet in HAWQ or will not because HDFS won’t allow it. And there are some features of HAWQ that don’t exist in Greenplum database that are also compelling.

## other stuff

https://hadoopecosystemtable.github.io/

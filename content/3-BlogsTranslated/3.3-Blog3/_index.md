---
title: "Gaming Developer's Guide to Amazon DocumentDB (with MongoDB compatibility) — Part 3: Operational Best Practices"
date: 2024-01-25
weight: 4
chapter: false
pre: " <b> 3.3. </b> "
---

Post date: Jan 25, 2024 – Authors: Jackie Jiang, Douglas Bonser, Matthew Nimmo in [Game Tech](https://aws.amazon.com/blogs/gametech/), [Databases](https://aws.amazon.com/blogs/database/), [Amazon DocumentDB](https://aws.amazon.com/blogs/database/category/database/amazon-documentdb/).

---

**Introduction**

Continuing our discussion on Amazon DocumentDB best practices from part two, this post focuses on data protection, scalability, monitoring, and cost optimization.

---

**Data Protection**

To protect data stored in Amazon DocumentDB, you should encrypt your data by enabling the storage encryption option when creating a cluster. Encryption is enabled by default for the entire cluster and applies to all instances, logs, automated backups, and snapshots. Amazon DocumentDB handles data encryption and decryption transparently with minimal impact on performance. You can use the default AWS key or provide your own key to encrypt your data.

Amazon DocumentDB supports Role-Based Access Control (RBAC), which should be used to restrict read-only access to specific databases or collections, as well as in multi-user application designs. The post [Introducing role-based access control for Amazon DocumentDB (with MongoDB compatibility)](https://aws.amazon.com/blogs/database/introducing-role-based-access-control-for-amazon-documentdb-with-mongodb-compatibility/) explains RBAC concepts and capabilities in Amazon DocumentDB in detail.

By using **AWS Secrets Manager**, you can programmatically retrieve Amazon DocumentDB passwords and automatically rotate them, replacing hardcoded credentials in source code, as described in [How to rotate Amazon DocumentDB and Amazon Redshift credentials in AWS Secrets Manager](https://aws.amazon.com/blogs/security/how-to-rotate-amazon-documentdb-and-amazon-redshift-credentials-in-aws-secrets-manager/).

**AWS CloudTrail** integrates with Amazon DocumentDB to provide a record of database actions taken by a user, role, or an AWS service, and captures all API calls for Amazon DocumentDB. See [Logging Amazon DocumentDB API Calls with AWS CloudTrail](https://docs.aws.amazon.com/documentdb/latest/developerguide/logging-using-cloudtrail.html) for more details.

Additionally, you can enable auditing in Amazon DocumentDB to record DDL, DML, authentication, authorization, and user management events to Amazon CloudWatch Logs in JSON document format. See [Auditing Amazon DocumentDB Events](https://docs.aws.amazon.com/documentdb/latest/developerguide/auditing.html) for more details.

---

**Scaling**

As mentioned in part one, Amazon DocumentDB supports both vertical and horizontal scaling. In this section, we dive deeper into read consistency, read preference, read and write traffic, dynamic read preference, and asymmetric workloads.

Let's explore **read consistency** and **read preference**. Reads from the primary instance have strong consistency, guaranteeing read-after-write consistency. Conversely, reads from replicas are eventually consistent. The lag between the primary and a replica is typically less than 100ms. To scale read capacity, you should use replica instances. This is done by setting `readPreference` to `secondaryPreferred`. In case a replica fails, the read request is redirected to the next available replica. Finally, if no replicas are available, reads are directed to the primary instance.

Now that we have an overview of how read consistency and preference work, let's talk about **scaling read traffic**. Suppose you have a cluster with three instances (one primary and two read replicas) and you want to scale to support high read traffic. You simply add read replicas! You can scale up to 15 read replicas per cluster. If you use `readPreference` as `secondaryPreferred`, the driver will automatically use the new replicas. Sometimes you might want to keep your default setting but override it on a per-query basis for higher consistency. For example, while your default points to `secondaryPreferred` read replicas, you can create an override query to fetch data directly from the "primary".

Although it is generally recommended to use homogenous instances in a cluster, you can still consider **asymmetric workloads**. For instance, if your workload has ad-hoc or periodic analytical needs like running monthly reports, you can size your cluster for online workloads and add a new node dedicated to analytics. From there, you run reporting queries on this new node, and when complete, you can shut it down to save costs.

We've discussed scaling for reads, but let's focus on the **write scaling** strategy! Suppose your write traffic increases or you anticipate it will. You are currently using a cluster of three `r6g.large` instances but want to move to `r6g.4xlarge`. First, you add three new `r6g.4xlarge` nodes to the cluster, and to be safe, you select a higher promotion tier for the larger nodes. Note that Amazon DocumentDB defaults to prioritizing larger nodes as primary. Now for the key part — you trigger an auto failover, and the larger instance will automatically be selected as primary. Once that happens, you can safely remove the smaller `r6g.large` instances. The figure below illustrates this process.

![Write Scaling](/images/3-BlogsTranslated/Blog4/img1.jpg)

Finally, let's wrap up the scaling topic by discussing **storage and I/O**. Both storage and I/O scale automatically in Amazon DocumentDB. Storage scales in 10GiB increments, up to a maximum of 128TiB. If you are migrating a workload to Amazon DocumentDB and plan to delete some data, such as historical data that is no longer needed, do so before migrating data to Amazon DocumentDB to reduce costs.

---

**Monitoring**

Monitoring in many AWS services is rich in detail and features, and Amazon DocumentDB is no exception. Let's overview the key areas covering the monitoring capabilities of this service.

**Amazon CloudWatch**

Amazon DocumentDB publishes over 50 operational metrics to CloudWatch that can be monitored. CloudWatch allows you to set alarms and send notifications when metrics exceed predefined values. These metrics provide information about:

-   **Instance**: `BufferCacheHitRatio`, `FreeableMemory`, etc.
-   **Cluster**: `DBClusterReplicaLagMaximum`, `VolumeWriteIOPS`, etc.
-   **Storage**: `VolumeBytesUsed`.
-   **Backup**: `SnapshotStorageUsed`, `TotalBackupStorageBilled`, etc.

If you want to dive deeper into Amazon DocumentDB CloudWatch metrics, check out [Monitoring metrics and setting up alarms on your Amazon DocumentDB clusters](https://aws.amazon.com/blogs/database/monitoring-metrics-and-setting-up-alarms-on-your-amazon-documentdb-clusters/) for details.

**Profiler and Auditing**

-   **What is the Profiler?** The Profiler helps you identify slow queries and discover opportunities to create new indexes. It also helps detect necessary optimizations for existing indexes to improve query performance. You set a threshold, and any operation running longer than that threshold is logged to CloudWatch Logs. You can use these logs to identify which queries are not using indexes or using suboptimal indexes. Ultimately, enabling the profiler helps you troubleshoot slow-running queries. See details at [Profiling Amazon DocumentDB Operations](https://docs.aws.amazon.com/documentdb/latest/developerguide/profiling.html).

-   **What is Auditing?** Auditing allows you to record certain events happening in Amazon DocumentDB. These events can include DDL events (authorization, user management, index creation, etc.) and DML events (create, read, update, delete). Since audit logs are written to CloudWatch Logs, you can set alarms for specific activities. For example: 10 failed login attempts within a minute. See details at [Introducing DML auditing for Amazon DocumentDB](https://aws.amazon.com/blogs/database/introducing-dml-auditing-for-amazon-documentdb-with-mongodb-compatibility/).

Profiler and auditing are disabled by default, so you need to enable and configure them before use. You can refer to the developer guide via these links:

-   [How to enable the profiler?](https://docs.aws.amazon.com/documentdb/latest/developerguide/profiling.html#profiling-enabling)
-   [How to enable auditing?](https://docs.aws.amazon.com/documentdb/latest/developerguide/auditing.html#auditing-enabling)

**Performance Insights**

Performance Insights extends Amazon DocumentDB's existing monitoring features to help you visualize cluster performance and analyze issues affecting it. With the Performance Insights dashboard, you can visualize database load, filter load by waits, query statements, hosts, or applications. Performance Insights is built-in with Amazon DocumentDB instances and retains 7 days of performance history at no additional cost. This feature is disabled by default and can be enabled per instance. For a quick demo, watch the video [Getting started with Amazon DocumentDB Observability and Monitoring](https://www.youtube.com/watch?v=EXAMPLE).

**Event Subscriptions**

Finally, you can subscribe to events occurring in Amazon DocumentDB. The service categorizes events into groups so you can subscribe to receive notifications when an event in that group occurs. Event categories include: cluster, instance, cluster snapshot, and parameter group. You can easily subscribe to all events in a category (e.g., all cluster events) or just a specific event from a specific resource (e.g., primary instance failover event in a production cluster). These events are created by default, requiring no additional configuration in Amazon DocumentDB. See details at [Using Amazon DocumentDB Event Subscriptions](https://docs.aws.amazon.com/documentdb/latest/developerguide/event-subscriptions.html).

---

**Cost Optimization**

Amazon DocumentDB charges per second of usage, with a 10-minute minimum charge. To proactively manage spending for DocumentDB clusters, you should create billing alarms at 50% and 75% thresholds of expected monthly costs. See the [Create a billing alarm](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/monitor_estimated_charges_with_cloudwatch.html) guide to learn how to create billing alarms. You can also track detailed costs by tagging clusters and instances. To understand how to track instance, storage, IOPS, and backup costs, read [Using cost allocation tags with Amazon DocumentDB](https://docs.aws.amazon.com/documentdb/latest/developerguide/tagging.html).

For non-production environments, you should stop all instances in the cluster (up to 7 days) when not needed, and restart them when work is required. When a cluster is stopped, you are only charged for storage, manual snapshots, and automated backups within the configured retention period. You are not charged for instance hours. See details at [Stopping and Starting an Amazon DocumentDB Cluster](https://docs.aws.amazon.com/documentdb/latest/developerguide/db-cluster-stop-start.html).

Amazon DocumentDB's design separates compute and storage. Data is replicated six times across three Availability Zones, ensuring high data durability regardless of the number of instances in the cluster. It is recommended to use a minimum of 3 instances for production environments to ensure high availability; whereas for test environments, you might only need 1 instance if downtime is acceptable.

Both **Time To Live indexes** and **change streams** create additional I/O operations when data is read, inserted, updated, or deleted. If your application does not use these features, disable them to reduce costs.

As your data grows, consider implementing an appropriate long-term data archival strategy to keep only active data in the cluster, while less accessed data can be stored in lower-cost storage options like Amazon S3. See the guide [Optimize data archival costs in Amazon DocumentDB using rolling collections](https://aws.amazon.com/blogs/database/optimize-data-archival-costs-in-amazon-documentdb-using-rolling-collections/) to understand how to implement this archival strategy.

When optimizing costs, don't forget backups. You cannot disable backups, with a retention period of minimum 1 day and maximum 35 days. Like other data resilience best practices, set the retention period based on your RPO (Recovery Point Objective). The backup window you define can also be used to automatically create development or test environments from snapshots. Finally, backing up data can take up to 5 minutes to capture the latest data, meaning you can restore data to any point in time from 5 minutes ago up to the end of the backup retention period.

---

**Examples**

To help you get started, here are links to example code. These include how to connect to Amazon DocumentDB using various popular programming languages, code from blogs, and AWS Lambda samples.

-   [How to connect to Amazon DocumentDB using various popular programming languages](https://docs.aws.amazon.com/documentdb/latest/developerguide/connect.html).
-   [AWS Lambda function samples](https://github.com/aws-samples/amazon-documentdb-samples/tree/master/lambda).
-   [Example code from other blog posts](https://github.com/aws-samples/amazon-documentdb-samples/tree/master/blogs).
-   [Official Amazon DocumentDB Samples GitHub repository](https://github.com/aws-samples/amazon-documentdb-samples).

---

**Conclusion**

In this post, we discussed best practices for managing and optimizing Amazon DocumentDB clusters. Many game developers are using Amazon DocumentDB to simplify the design and management of backend database systems powering their games. By adopting the practices outlined in this post, you can get started smoothly and successfully deploy Amazon DocumentDB.

To learn more about Amazon DocumentDB, you can follow videos in the **Amazon DocumentDB Insider Hour**, which shares insights on the well-architected lens, workshops, migration processes, and new releases. Additionally, you can access the **Amazon DocumentDB Tools** GitHub for use during assessment and data migration.

---

### About the Authors

| Image                                                          | Bio                                                                                                                                                                                                                                              |
| :------------------------------------------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ![Jackie Jiang](/images/3-BlogsTranslated/Blog4/author1.jpg)   | **Jackie Jiang**: Jackie is a Senior Database Specialist Solutions Architect at AWS. She works with key customers on database strategy, database migration, and Amazon DocumentDB best practices.                                                |
| ![Douglas Bonser](/images/3-BlogsTranslated/Blog4/author2.jpg) | **Douglas Bonser**: Douglas is a Senior Solutions Architect at AWS, specializing in supporting Game Tech customers. He has a background in software development and is passionate about helping game studios build and scale their games on AWS. |
| ![Matthew Nimmo](/images/3-BlogsTranslated/Blog4/author3.jpg)  | **Matthew Nimmo**: Matthew is a Sr. Solutions Architect at AWS. He works with the world's largest gaming companies to help them build, deploy, and scale games in the cloud.                                                                     |

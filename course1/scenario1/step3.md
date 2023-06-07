# CockroachDB Monitoring  with DB Console

## DB Console 

The [DB Console](https://www.cockroachlabs.com/docs/stable/ui-overview.html) provides details & metrics about your cluster and database configuration, and helps you optimize cluster performance.

### a) Overview Page 


The Overview page provides a cluster overview and node list and map.

- `Cluster Overview` has essential metrics about the cluster and nodes, including liveness status, replication status, uptime, and hardware usage.
- `Node List` has a list of cluster metrics at the locality and node levels. You should see the below.
    - `localhost:26257 (n1)`
    - `localhost:26258 (n2)`
    - `localhost:26259 (n3)`

### b) Metrics Page
The Metrics page provides dashboards for all types of CockroachDB metrics.

- `Overview dashboard` has metrics about SQL performance, replication, and storage.
- `Hardware dashboard` has metrics about CPU usage, disk throughput, network traffic, storage capacity, and memory.
- `Runtime dashboard` has metrics about node count, CPU time, and memory usage.
- `SQL dashboard` has metrics about SQL connections, byte traffic, queries, transactions, and service latency.
- `Storage dashboard` has metrics about storage capacity and file descriptors.
- `Replication dashboard` has metrics about how data is replicated across the cluster, e.g., range status, replicas per store, and replica quiescence.
- `Distributed dashboard` has metrics about distribution tasks across the cluster, including RPCs, transactions, and node heartbeats.
- `Queues dashboard` has metrics about the health and performance of various queueing systems in CockroachDB, including the garbage collection and Raft log queues.
- `Slow requests dashboard` has metrics about important cluster tasks that take longer than expected to complete, including Raft proposals and lease acquisitions.
- `Changefeeds dashboard` has metrics about the changefeeds created across your cluster.
- `Overload dashboard` has metrics about the performance of the parts of your cluster relevant to the cluster's admission control system.
- `TTL dashboard` has metrics about the progress and performance of batch deleting expired data using Row-Level TTL from your cluster.

Note :  Follow the [DB Console](https://www.cockroachlabs.com/docs/stable/ui-overview.html) link to learn more about the features of DB Console. 

End of module 1
----





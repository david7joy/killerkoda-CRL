# Test Resiliency of the CockroachDB Cluster


##  Killing a CockroachDB Node

a) Bring down the node with SQL port 26257, Kill the process id for the first CockroachDB node.

```
kill -9 $(ps -eaf | grep -v "grep" | grep node1 | awk '{print $2}')
```{{exec}}

b) Run a workload towards SQL Port 26258

Execute a new workload on the next available SQL port and notice that CockroachDB continues to run

```
cockroach workload run movr --duration=3m 'postgresql://root@localhost:26258?sslmode=disable'
```{{exec}}

c) Monitor DB Console on [CockroachDB UI Port 8082]({{TRAFFIC_HOST1_8082}})

You will notice that one node is unavailable, however, transactions continue to process on CockroachDB on other nodes. 

Notice that the SQL statements provide activity for the two remaining nodes and also give the Service Latency percentiles while the node is down.
# Run CockroachDB Workload & Monitor

a) Initialize the CockroachDB workload called `movr`

```
cockroach workload init movr 'postgresql://root@localhost:26257?sslmode=disable'
```{{exec}}

b) Access the SQL console to see the `movr` database and run a query

```
cockroach sql --insecure
```{{exec}}

```
SHOW TABLES FROM movr;
```{{exec}}

```
SELECT * FROM movr.users WHERE city='new york';
```{{exec}}

c) Exit the CockroachDB SQL console

```
exit
```{{exec}}

d) Run a workload with duration of `1m` against the cluster via the first node with SQL port `26257`

```
cockroach workload run movr --duration=1m 'postgresql://root@localhost:26257?sslmode=disable'
```{{exec}}

e) Check the activity at [CockroachDB UI Port 8081]({{TRAFFIC_HOST1_8081}}/#/metrics/overview/cluster) to determine the Service Latency with 3 nodes.

----
End of Module 2
----
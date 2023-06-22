# Test Resiliency of the CockroachDB Cluster

##  Adding a CockroachDB Node

a) Bring back up the node 

```
cockroach start \
    --insecure \
    --store=node1 \
    --listen-addr=localhost:26257 \
    --http-addr=0.0.0.0:8081 \
    --join=localhost:26257,localhost:26258,localhost:26259 \
    --background
```{{exec}}

b) Let's see the activity in the UI console: [CockroachDB UI Port 8081]({{TRAFFIC_HOST1_8081}}) or [CockroachDB UI Port 8082]({{TRAFFIC_HOST1_8082}})

Now you have learned how resilient cockroachDB is and how easy it is to scale / upgrade nodes in CockroachDB without effecting Application experience to end users. 

----
End of Module 3
----
 
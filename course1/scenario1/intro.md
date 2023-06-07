The current workshop will help you deploy an insecure (no-SSL) CockroachDB cluster step by step. 

## Workshop Objectives:

- Download the latest binary (or a specific release). See releases listed in [CockroachDB Github](https://github.com/cockroachdb/cockroach/tags)
- Deploy 3 nodes, one by one, in the same host. Best practices are to deploy one CockroachDB instance per VM.
- Monitor the activity of the cluster via either UI port:
    - CockroachDB UI Port 8081({{TRAFFIC_HOST1_8081}})
- Run the movr small workload & SQL queries that list the activity in the cluster.
- Remove a node from the cluster and add another node to the cluster.

Note:  We are going to create 3 nodes on a single ubunto server. Running multiple nodes on a single host is helpful for testing CockroachDB, but it's not suitable for production.
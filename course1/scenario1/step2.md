## Start the cluster

a) Use the cockroach start command to start the first node:

```
cockroach start \
    --insecure \
    --store=node3 \
    --listen-addr=localhost:26259 \
    --http-addr=localhost:8082 \
    --join=localhost:26257,localhost:26258,localhost:26259 \
    --background
```{{exec}}

b) Take a moment to understand the flags you used:

   -  The `--insecure` flag makes communication unencrypted.
    - Since this is a purely local cluster, `--listen-addr=localhost:26257` and `--http-addr=localhost:8080` tell the node to listen only on `localhost`, with port `26257` used for internal and client traffic and port `8080` used for HTTP requests from the DB Console.
    - The `--store` flag indicates the location where the node's data and logs are stored.
    - The `--join` flag specifies the addresses and ports of the nodes that will initially comprise your cluster. You'll use this exact `--join` flag when starting other nodes as well.

        For a cluster in a single region, set 3-5 `--join` addresses. Each starting node will attempt to contact one of the join hosts. In case a join host cannot be reached, the node will try another address on the list until it can join the gossip network.

- The `--background` flag starts the `cockroach` process in the background so you can continue using the same terminal for other operations.

b) Download the CockroachDB archive for Linux, and extract the binary:
    
`curl https://binaries.cockroachdb.com/cockroach-v23.1.1.linux-amd64.tgz | tar -xz`{{exec}}

c) Start two more nodes:

Note: These commands are the same as before but with unique --store, --listen-addr, and --http-addr flags. The node names are different and the ports are different too. The reason for 8081 and 8082 is because we are running this locally for testing. In production this will be different.

```
cockroach start \
    --insecure \
    --store=node2 \
    --listen-addr=localhost:26258 \
    --http-addr=localhost:8081 \
    --join=localhost:26257,localhost:26258,localhost:26259 \
    --background
```{{exec}}

```
cockroach start \
    --insecure \
    --store=node3 \
    --listen-addr=localhost:26259 \
    --http-addr=localhost:8082 \
    --join=localhost:26257,localhost:26258,localhost:26259 \
    --background
```{{exec}}

d) Use the cockroach init command to perform a one-time initialization of the cluster, sending the request to any node on the --join list:

`cockroach init --insecure --host=localhost:26257`{{exec}}

You'll see the following message:

`Cluster successfully initialized`

At this point, each node also prints helpful startup details to its log. For example, the following command retrieves node 1's startup details:

`grep 'node starting' node1/logs/cockroach.log -A 11`

The output will look something like this:

    ```
    CockroachDB node starting at 
    build:               CCL v23.1.1 @ 2023-05-16 00:00:00 (go1.19) (go1.12.6)
    webui:               http://localhost:8080
    sql:                 postgresql://root@localhost:26257?sslmode=disable
    RPC client flags:    cockroach <client cmd> --host=localhost:26257 --insecure
    logs:                /Users/<username>/node1/logs
    temp dir:            /Users/<username>/node1/cockroach-temp242232154
    external I/O path:   /Users/<username>/node1/extern
    store[0]:            path=/Users/<username>/node1
    status:              initialized new cluster
    clusterID:           8a681a16-9623-4fc1-a537-77e9255daafd
    nodeID:              1
    ```

e) Check The Cluster has started status

`cockroach node status --insecure`{{exec}}

This should show 3 nodes running in a cluster.

 
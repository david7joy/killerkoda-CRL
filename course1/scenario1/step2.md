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

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

### Execute multiline code block

```
uname -r
pwd
```{{exec}}

### Copy multiline code block
```
cockroach start \
    --insecure \
    --store=node3 \
    --listen-addr=localhost:26259 \
    --http-addr=localhost:8082 \
    --join=localhost:26257,localhost:26258,localhost:26259 \
    --background
```{{copy}}

### Execute multiline code block

```
uname -r
pwd
```{{exec}}

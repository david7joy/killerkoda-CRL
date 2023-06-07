### Download cockroachDB Binary

1. Use the cockroach start command to start the first node:

    a) Set path 
    
    `cd /home/ubuntu`{{exec}}

    b) Download the CockroachDB archive for Linux, and extract the binary:
    
    `curl https://binaries.cockroachdb.com/cockroach-v23.1.1.linux-amd64.tgz | tar -xz`{{exec}}

    c) Copy the binary into the PATH:
    
    `cp -i cockroach-v23.1.1.linux-amd64/cockroach /usr/local/bin/`{{exec}}

    If you get a permissions error, prefix the command with sudo.

2. CockroachDB uses custom-built versions of the GEOS libraries. Copy these libraries to one of the locations where CockroachDB expects to find them.

    a) Create the directory where the external libraries will be stored:

    `mkdir -p /usr/local/lib/cockroach`{{exec}}

    b) Copy the library files to the directory:

    `cp -i cockroach-v23.1.1.linux-amd64/lib/libgeos.so /usr/local/lib/cockroach/`{{exec}}

    `cp -i cockroach-v23.1.1.linux-amd64/lib/libgeos_c.so /usr/local/lib/cockroach/`{{exec}}

    If you get a permissions error, prefix the command with sudo.

3. Verify that CockroachDB can execute spatial queries.

    a) Make sure the cockroach binary you just installed is the one that runs when you type cockroach in your shell:

    `which cockroach`{{exec}}

    ```
    /usr/local/bin/cockroach
    ```

    b) Start a temporary, in-memory cluster using cockroach demo:

    `cockroach demo`{{exec}}

    c) In the demo cluster's interactive SQL shell, run the following command to test that the spatial libraries have loaded properly:

    `SELECT ST_IsValid(ST_MakePoint(1,2));`{{exec}}

    You should see the following output:

    ```
    st_isvalid
    --------------
    true
    (1 row)
    ```

    If your cockroach binary is not properly accessing the dynamically linked C libraries in /usr/local/lib/cockroach, it will output an error message like the one below.

    ```
    ERROR: st_isvalid(): geos: error during GEOS init: geos: cannot load GEOS from dir "/usr/local/lib/cockroach": failed to execute dlopen
          Failed running "sql"
    ```

    d) let's exit from cockroach sql shell
    
    ```
    exit
    ```{{exec}}
# Killercoda Scenario Examples Courses

See these in action here: https://killercoda.com/examples-courses

Documentation: https://killercoda.com/creators

ubuntu $ cockroach start --insecure --store=node1 --listen-addr=localhost:26257 --http-addr=localhost:8080 --join=localhost:26257,localhost:26258,localhost:26259 --background


## Structure

Scenarios in a subdirectory are considered a group/course.

Once a `structure.json` is available, only the information from that file will be used.

Any scenario or directory that exists outside the `structure.json` will be ignored.

For example: the `/scenario1` is not included here.

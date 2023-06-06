## Using Cockroachdb

a) Launch the built-in SQL client, with the --host flag set to the address of the load balancer:

```cockroach sql --insecure
```{{exec}}

b) Lets create a new database called `GameData`

```
CREATE DATABASE GameData;
```{{exec}}

c) View the cluster's databases, which will include `GameData``:

```
SHOW DATABASES'
```{{exec}}

d) Creata a table `users` in database `GameData`:

```
USE GameData
```{{exec}}

```
CREATE TABLE users (
  id UUID NOT NULL,
  username VARCHAR(128) NOT NULL,
  display_name VARCHAR(255) NULL,
  avatar_url VARCHAR(512) NULL,
  lang_tag VARCHAR(18) NOT NULL DEFAULT 'en':::STRING,
  location VARCHAR(255) NULL,
  timezone VARCHAR(255) NULL,
  metadata JSONB NOT NULL DEFAULT '{}':::JSONB,
  wallet JSONB NOT NULL DEFAULT '{}':::JSONB,
  email VARCHAR(255) NULL,
)
```{{exec}}

e) Insert some data into table `users` in database `GameData`:

f) delete some data from the table `users` in database `GameData: 

g) update `users` in database `GameData`
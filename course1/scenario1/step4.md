# Running queries on Cockroachdb 

a) Launch the built-in SQL client, with the --host flag set to the address of the load balancer:

```
cockroach sql --insecure
```{{exec}}

b) Lets create a new database called `GameData`

```
CREATE DATABASE GameData;
```{{exec}}

c) View the cluster's databases, which will include `GameData``:

```
SHOW DATABASES;
```{{exec}}

d) Creata a table `users` in database `GameData`:

```
USE GameData;
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
  email VARCHAR(255) NULL);
```{{exec}}

```
show tables;
```{{exec}}

e) Insert some data into table users in database GameData :

INSERT INTO users (id, username, display_name, avatar_url, lang_tag, location, timezone, metadata, wallet, email) VALUES ('33a57d9c-0efa-4aa0-99cb-9eecb876fef1', 'ptaffley0', 'Phylis', 't-online.de/faucibus.xml', 'New Zealand Sign Language', 'Kuantan', 'Asia/Kuala_Lumpur', '[{},{},{},{}]', '[{},{},{}]', 'pitshak0@addtoany.com');
INSERT INTO users (id, username, display_name, avatar_url, lang_tag, location, timezone, metadata, wallet, email) VALUES ('8b552393-46ae-4cdc-a6af-1b49ca0ba6d5', 'mwollaston3', 'Merralee', 'godaddy.com/aliquet/at/feugiat/non/pretium.xml', 'German', 'Nāḩiyat as Sab' Biyār', 'Asia/Damascus', '[{},{}]', '[{},{}]', 'mtrymme3@earthlink.net');
INSERT INTO users (id, username, display_name, avatar_url, lang_tag, location, timezone, metadata, wallet, email) VALUES ('74ff5a98-c8f9-4c50-8954-0d5b1b63a34c', 'educkitt7', 'Ethe', 'comsenz.com/rhoncus/aliquet.jsp', 'Zulu', 'Cache Creek', 'America/Vancouver', '[{},{},{}]', '[{},{}]', 'egerrard7@ocn.ne.jp');

SELECT * FROM users;

f) delete some data from the table users in database GameData:

DELETE FROM users WHERE username = 'educkitt7';

SELECT * FROM users;

g) update users in database GameData:

UPDATE users SET lang_tag = 'EN' WHERE username = 'mwollaston3';

SELECT * FROM users;

h) let's exit from cockroach sql shell
```
exit
```{{exec}}
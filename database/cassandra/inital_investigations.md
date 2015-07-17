# Bug
1. Tested the clustering on the same subnet.
2. Installed natively to the OS.
3. configured both nodes to be in the same cluster.
3. ingested data into one node.
4. verified data replicates no issues.

# Config
vi /etc/yum.repos.d/datastax.repo

```
[datastax]
name = DataStax Repo for Apache Cassandra
baseurl = http://rpm.datastax.com/community
enabled = 1
gpgcheck = 0
```

Run the following:

```
yum install -y dsc20 which vim

systemctl stop firewalld
```

## Before you start Cassandra!
- Edit Cassandra configuration file. ```/etc/cassandra/conf/cassandra.yaml```
    + listen_address:
    + rpc_address: $IP_OF_MACHINE
    + seeds: <csv - list of seeds we wanted>

## Start Cassandra
```systemctl start cassandra```
- checked ```/var/log/cassandra/system.log``` and cassandra.log for errors

## Ingest data
- use ```cqlsh``` to create testing tables

```
CREATE KEYSPACE mykeyspace
WITH REPLICATION = { 'class' : 'SimpleStrategy', 'replication_factor' : 1 };

USE mykeyspace;

CREATE TABLE users (
  user_id int PRIMARY KEY,
  fname text,
  lname text
);
INSERT INTO users (user_id,  fname, lname)
  VALUES (1745, 'john', 'smith');
INSERT INTO users (user_id,  fname, lname)
  VALUES (1744, 'john', 'doe');
INSERT INTO users (user_id,  fname, lname)
  VALUES (1746, 'john', 'smith');

SELECT * FROM users;
```

```
for j in `seq 1 200`; do unset INSERT_STRING && for i in `seq 1 100`; do NEW_UUID=$(cat /dev/urandom | tr -dc 'a-zA-Z0-9' | fold -w 32 | head -n 1) && INSERT_STRING="$INSERT_STRING INSERT INTO users (user_id,  fname, lname)
 VALUES ($(($i*$j)), '$NEW_UUID', 'smith');"; done && cqlsh 10.20.88.252 -e "use mykeyspace; $INSERT_STRING" && unset INSERT_STRING; done
```

# More feedback.
1. Implement database schema creation.
    * [Quick start](http://www.datastax.com/documentation/developer/java-driver/2.1/java-driver/quick_start/qsSimpleClientAddSession_t.html)
2. Encrypting communication between instances of Cassandra.
    * [node to node encryption](http://www.datastax.com/documentation/cassandra/1.2/cassandra/security/secureSSLNodeToNode_t.html)
3. Links
    * [Ebay](http://www.ebaytechblog.com/2012/07/16/cassandra-data-modeling-best-practices-part-1/#.VCQ4kBbMoXI)
    * [Netflix](http://www.slideshare.net/nkorla1share/cass-summit-3)

4. Common to see read latency
    * I saw the start of the read latency with only 7260 rows.

# Notes
* http://www.datastax.com/documentation/cassandra/2.1/cassandra/install/installRecommendSettings.html
* http://kkovacs.eu/cassandra-vs-mongodb-vs-couchdb-vs-redis
* http://planetcassandra.org/apache-cassandra-use-cases/
*  http://www.ebaytechblog.com/2012/07/16/cassandra-data-modeling-best-practices-part-1/#.VCQ4kBbMoXI
* http://www.slideshare.net/nkorla1share/cass-summit-3

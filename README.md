
# docker-hbase
Forked from  [docker-hbase](https://github.com/big-data-europe/docker-hbase)

# Only Hadoop
To run standalone Hadoop 
```
docker-compose -f docker-compose-standalone.yml up -d
```
* [Namenode WebUI](http://localhost:9870/)
* [Datanode WebUI](http://localhost:9864/)
* [Yarn WebUI](http://localhost:8088/)

Test:
```
docker cp ./tests/WordCount.jar namenode:/
docker exec -it namenode bash
echo 'test' > test.txt
hadoop dfs -put ./test.txt  /
hadoop jar WordCount.jar WordCount /test.txt /output
hadoop dfs -cat /output/*
```
The result will be `test    1`

# Add Hive
TODO
# Add Spark
TODO
# Add Hbase
To run standalone Hbase:
```
docker-compose -f docker-compose-hbase-standalone.yml up -d
```
The deployment is the same as in [quickstart HBase documentation](https://hbase.apache.org/book.html#quickstart).
Can be used for testing/development, connected to Hadoop cluster.

Hbase Shell Test:
```
docker exec -it hbase bash
hbase shell
list
create 'test', 'cf'
put 'test', 'row1', 'cf:col1', 'value1'
get 'test', 'row1'
list
```
It should be working.

* [Hbase WebUI](http://localhost:16010/)

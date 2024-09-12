
**Set up Kafka --**

Create 2 folders in F drive--
kafka_logs-- zookeeper
kafka_logs-- server_logs

change the zookeeper.properties:
------------------------------------------------------
dataDir=C:/kafka_logs/zookeeper
maxClientCnxns=1

This property limits the number of active connections from a host, specified by IP address, to a single ZooKeeper server.

change the server.properties:
----------------------------------------------------
uncomment listeners
log.dirs=C:/kafka_logs/server_logs
zookeeper.connect=localhost:2181
zookeeper.connection.timeout.ms=60000

Start Zookeeper:
---------------------------------------
C:/Kafka/bin/windows/zookeeper-server-start.bat C:/Kafka/config/zookeeper.properties

Start Kafka-server:
-----------------------------------------
C:/Kafka/bin/windows/kafka-server-start.bat C:/Kafka/config/server.properties

Create topic:
------------------------------------
C:/Kafka/bin/windows/kafka-topics.bat --create --topic hello_world --bootstrap-server localhost:9092 --replication-factor 1 --partitions 1

Start Producer:
--------------------------------------
C:/Kafka/bin/windows/kafka-console-producer.bat --topic hello_world --bootstrap-server localhost:9092

#Start Consumer:
-------------------------------------
C:/Kafka/bin/windows/kafka-console-consumer.bat --topic hello_world --from-beginning --bootstrap-server localhost:9092


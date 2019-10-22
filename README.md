# wg-base-kafka

|    hostName     | IP       | port   | listener |
| -----------     | -------- | ------ | ------  |
| zookeeper1 | 172.19.0.11 | 2184:2181 |  | 
| zookeeper1 | 172.19.0.12 | 2185:2181 |  | 
| zookeeper1 | 172.19.0.13 | 2186:2181 |  | 
| kafka1 | 172.19.0.14 | 9092:9092 | kafka1 | 
| kafka2 | 172.19.0.15 | 9093:9092 | kafka2 | 
| kafka3 | 172.19.0.16 | 9094:9092| kafka3 | 

```
1.docker network ls
2.docker network create --driver bridge --subnet 172.19.0.0/16 --gateway 172.19.0.1 zookeeper_network
3.docker nerwork inspect  zookeeper_network
4.docker network rm zookeeper_network

topic
5.docker exec -ti kafka1 bash  (windows: winpty docker exec -it d437 bash) 
6../kafka-topics.sh --create --zookeeper localhost:2184,localhost:2185,localhost:2186 --replication-factor 1 --partitions 1 --topic wg_message
   //localhost 改为宿主机IP

```

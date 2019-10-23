# wg-base-kafka

##### hosts文件
- 10.4.137.102 为宿主机IP
- hosts 
```
10.4.137.102 kafka1
10.4.137.102 kafka2
10.4.137.102 kafka3
```

##### IP,Ports 

|    hostName     | IP       | port   | listener |
| -----------     | -------- | ------ | ------  |
| zookeeper1 | 172.19.0.11 | 2184:2181 |  | 
| zookeeper1 | 172.19.0.12 | 2185:2181 |  | 
| zookeeper1 | 172.19.0.13 | 2186:2181 |  | 
| kafka1 | 172.19.0.14 | 9092:9092 | kafka1 | 
| kafka2 | 172.19.0.15 | 9093:9092 | kafka2 | 
| kafka3 | 172.19.0.16 | 9094:9092| kafka3 | 

##### cluster
- docker network
```

1. docker network ls
2. docker network create --driver bridge --subnet 172.19.0.0/16 --gateway 172.19.0.1 zookeeper_network
3. docker nerwork inspect  zookeeper_network
4. docker network rm zookeeper_network
```
- topic
```
5. docker exec -ti kafka1 bash  (windows: winpty docker exec -it d437 bash) 
6. ./kafka-topics.sh --create --zookeeper localhost:2184,localhost:2185,localhost:2186 --replication-factor 1 --partitions 1 --topic wg_base_message
   //localhost 改为宿主机IP
  ./kafka-topics.sh --create --zookeeper 10.4.137.102:2184,10.4.137.102:2185,10.4.137.102:2186 --replication-factor 1 --partitions 1 --topic wg_base_message
7. ./kafka-topics.sh --list --zookeeper 10.4.137.102:2184,10.4.137.102:2185,10.40.137.102:2186
8. ./kafka-topics.sh --delete --zookeeper 10.4.137.102:2184,10.4.137.102:2185,10.40.137.102:2186 --topic wg_base_message
9. ./kafka-console-producer.sh --broker-list 10.4.137.102:9092,10.4.137.102:9093,10.40.137.102:9094 --topic wg_base_message
10.  ./kafka-console-consumer.sh --bootstrap-server 10.4.137.102:9092,10.4.137.102:9093,10.40.137.102:9094 --topic wg_base_message  --from-beginning
```

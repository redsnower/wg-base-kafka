# wg-base-kafka
```
1.docker network ls
2.docker network create --driver bridge --subnet 172.19.0.0/16 br17219
3.docker nerwork inspect  br17219
4.docker network rm br17219

topic
5.docker exec -ti kafka1 bash  (windows: winpty docker exec -it d437 bash) 
6../kafka-topics.sh --create --zookeeper localhost:2184,localhost:2185,localhost:2186 --replication-factor 1 --partitions 1 --topic test1

```

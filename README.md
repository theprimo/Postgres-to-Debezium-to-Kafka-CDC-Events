step1:
enable Hiper-V option in Windows, for Docker desktop

step2:
place below 3 under a folder
1. connector
2. docker-compose.yaml
3. initdb.sql

step3:
goto the folder n open windows powershell and run below command
docker-compose up --build

step4: insert or update db records n watch cdc event log msgs in kafka topic
docker run -it --net=part1_default -e ZOOKEEPER_CONNECT=zookeeper1:2181 -e KAFKA_BROKER=kafka1:9092 --name watcher --rm --link part1_zookeeper1_1:part1_zookeeper1_1 --link part1_kafka1_1:part1_kafka1_1 debezium/kafka watch-topic -a -k dbserver1.public.dumb_table

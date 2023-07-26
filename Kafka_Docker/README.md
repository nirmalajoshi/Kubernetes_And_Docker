1. Launch zookeeper and kafka broker

docker-compose -f Single_Kafka_Broker.yml up -d

2.check if services are running

docker-compose -f Single_Kafka_Broker.yml ps

example: 
NAME                IMAGE                             COMMAND                  SERVICE             CREATED              STATUS              PORTS
kafka1              confluentinc/cp-kafka:7.3.2       "/etc/confluent/dock…"   kafka1              About a minute ago   Up About a minute   0.0.0.0:9092->9092/tcp, 0.0.0.0:9999->9999/tcp, 0.0.0.0:29092->29092/tcp
zoo1                confluentinc/cp-zookeeper:7.3.2   "/etc/confluent/dock…"   zoo1                About a minute ago   Up About a minute   2888/tcp, 0.0.0.0:2181->2181/tcp, 3888/tcp

here kafka will be exposed at localhost:9092

3.Running commands from kafka docker container

docker exec -it kafka1 /bin/bash, 

Then within container you can run kafka commands without .sh extension

example: kafka topics --version

Note:To run commands outside container you need to install the kafka binaries on system.

4. To stop kafka

docker-compose -f zk-single-kafka-single.yml stop

5.To remove all the resources including the containers altogether, use down instead of stop

docker-compose -f zk-single-kafka-single.yml down

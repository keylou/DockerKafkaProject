# DockerKafkaProject
Проект по знакомству с Docker и Message Broker

Команды: которые нужно вписать в консоль после запуска программы:

cd /Users/.../src/main/docker/kafka

docker-compose up

docker exec -it broker bash

kafka-topics --bootstrap-server localhost:9092 --topic orders-by-user --delete
kafka-topics --bootstrap-server localhost:9092 --topic discount-profiles-by-user --delete
kafka-topics --bootstrap-server localhost:9092 --topic discounts --delete
kafka-topics --bootstrap-server localhost:9092 --topic orders --delete
kafka-topics --bootstrap-server localhost:9092 --topic payments --delete
kafka-topics --bootstrap-server localhost:9092 --topic paid-orders --delete


kafka-topics \
  --bootstrap-server localhost:9092 \
  --topic orders-by-user \
  --create
kafka-topics \
  --bootstrap-server localhost:9092 \
  --topic discount-profiles-by-user \
  --create \
  --config "cleanup.policy=compact"
kafka-topics \
  --bootstrap-server localhost:9092 \
  --topic discounts \
  --create \
  --config "cleanup.policy=compact"
kafka-topics \
  --bootstrap-server localhost:9092 \
  --topic orders \
  --create
kafka-topics \
  --bootstrap-server localhost:9092 \
  --topic payments \
  --create
kafka-topics \
  --bootstrap-server localhost:9092 \
  --topic paid-orders \
  --create

kafka-console-producer \
   --topic discounts \
   --broker-list localhost:9092 \
   --property parse.key=true \
   --property key.separator=,
profile1,{"profile":"profile1","amount":0.5}
profile2,{"profile":"profile2","amount":0.25}
profile3,{"profile":"profile3","amount":0.15}

kafka-console-producer \
   --topic discount-profiles-by-user \
   --broker-list localhost:9092 \
   --property parse.key=true \
   --property key.separator=,
Daniel,profile1
Leo,profile2

kafka-console-producer \
   --topic orders-by-user \
   --broker-list localhost:9092 \
   --property parse.key=true \
   --property key.separator=,
Daniel,{"orderId":"order1","userId":"Daniel","products":["iPhone 13","MacBook Pro 15"],"amount":4000.0}
Leo,{"orderId":"order2","userId":"Leo","products":["iPhone 11"],"amount":800.0}

kafka-console-producer \
   --topic payments \
   --broker-list localhost:9092 \
   --property parse.key=true \
   --property key.separator=,
order1,{"orderId":"order1","status":"PAID"}
order2,{"orderId":"order2","status":"PENDING"}

kafka-console-consumer \
    --bootstrap-server localhost:9092 \
    --topic paid-orders \
    --from-beginning

# DockerKafkaProject
Проект по знакомству с Docker и Message Broker

Команды: которые нужно вписать в консоль после запуска программы:
```
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
```

# Результат работы кода.

<img width="482" alt="image" src="https://github.com/user-attachments/assets/546a2356-dae2-476c-b08e-8853a124dd11">
<img width="482" alt="image" src="https://github.com/user-attachments/assets/52295ebb-8c8b-446e-b6fb-8e71303219be">
<img width="482" alt="image" src="https://github.com/user-attachments/assets/10bd9e42-da9a-466e-b16e-7d5742bbff6f">
<img width="482" alt="image" src="https://github.com/user-attachments/assets/ee73721d-ffbf-48e9-b9e1-f54df4a0a5a5">
<img width="482" alt="image" src="https://github.com/user-attachments/assets/59aae2f7-dc55-46a3-8dc4-bdc9c93068d9">



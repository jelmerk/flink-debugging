1. create a custom version of flink that includes prometheus

       docker build -t ecg/flink_1.4.0-prometheus-hadoop28-scala_2.11 docker

2. Bring up zookeeper, kafka and flink

       docker-compose up -d
       
3. Build the job

       mvn clean package
 
4. Deploy the job a few times

       docker exec -it flink /opt/flink/bin/flink run -q -d /app/flink-app-1.0.jar implode1
       docker exec -it flink /opt/flink/bin/flink run -q -d /app/flink-app-1.0.jar implode2
       docker exec -it flink /opt/flink/bin/flink run -q -d /app/flink-app-1.0.jar implode3

4. View the flink console output 

       docker-compose logs -f -t flink
       
5. Send some messages to the kafka topic

   Leave the console output running then in another terminal start the console producer 

       docker exec -it kafka /opt/kafka/bin/kafka-console-producer.sh --topic mytopic --broker-list kafka:9092
       
   Enter the following lines of text
   
       message 1
       message 2
   
   If you look at your other terminal these messages should be in the console output
   
6. Check the prometheus endpoints

       curl http://localhost:9249/
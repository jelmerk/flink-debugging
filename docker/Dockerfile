FROM  flink:1.4.0-hadoop28-scala_2.11

WORKDIR /opt/flink/

RUN cp /opt/flink/opt/flink-metrics-prometheus-1.4.0.jar /opt/flink/lib
RUN apt-get update && apt-get install openjdk-8-jdk-headless

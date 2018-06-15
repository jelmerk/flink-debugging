FROM  flink:1.4.2-hadoop26-scala_2.11

RUN cp /opt/flink/opt/flink-metrics-prometheus-1.4.2.jar /opt/flink/lib
RUN apt-get update && apt-get -y install openjdk-8-jdk-headless && apt-get -y install iptables && apt-get -y install htop && apt-get -y install tcpdump && apt-get -y install procps

ADD flink-openstack-fs-hadoop-1.4.2.jar /opt/flink/lib/flink-openstack-fs-hadoop-1.4.2.jar

ENV TINI_VERSION v0.16.1
ADD https://github.com/krallin/tini/releases/download/${TINI_VERSION}/tini /tini
RUN chmod +x /tini
ENTRYPOINT ["/tini", "--", "/docker-entrypoint.sh"]

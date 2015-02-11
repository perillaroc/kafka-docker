FROM docker.cn/docker/centos:7

MAINTAINER Perilla Roc <perillaroc@gmail.com>

RUN yum install -y wget tar unzip java-1.7.0-openjdk-headless.x86_64

RUN wget http://mirrors.cnnic.cn/apache/kafka/0.8.2.0/kafka_2.10-0.8.2.0.tgz
RUN tar xzf kafka_2.10-0.8.2.0.tgz -C /opt

EXPOSE 9092

ENV KAFKA_HOME /opt/kafka_2.10-0.8.2.0
WORKDIR /opt/kafka_2.10-0.8.2.0

RUN sed -i -r 's/^(zookeeper.connect)=(.*)/\1=10.28.32.175:2181/g' $KAFKA_HOME/config/server.properties
RUN sed -i -r 's/(^|^#)(advertised.host.name)=(.*)/\2=10.28.32.175/g' $KAFKA_HOME/config/server.properties
CMD $KAFKA_HOME/bin/kafka-server-start.sh $KAFKA_HOME/config/server.properties

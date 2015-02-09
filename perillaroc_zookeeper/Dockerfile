FROM docker.cn/docker/centos:7

MAINTAINER Perilla Roc <perillaroc@gmail.com>

RUN yum install -y wget tar unzip java-1.7.0-openjdk-headless.x86_64
RUN wget http://mirrors.cnnic.cn/apache/zookeeper/zookeeper-3.4.6/zookeeper-3.4.6.tar.gz
RUN tar xzf zookeeper-3.4.6.tar.gz -C /opt
RUN mv /opt/zookeeper-3.4.6/conf/zoo_sample.cfg /opt/zookeeper-3.4.6/conf/zoo.cfg

ENV ZK_HOME /opt/zookeeper-3.4.6

RUN sed -i "s|/tmp/zookeeper|$ZK_HOME/data|g" $ZK_HOME/conf/zoo.cfg; mkdir $ZK_HOME/data
RUN sed -i -r 's|#(log4j.appender.ROLLINGFILE.MaxBackupIndex.*)|\1|g' $ZK_HOME/conf/log4j.properties
RUN sed -i -r 's|#autopurge|autopurge|g' $ZK_HOME/conf/zoo.cfg

EXPOSE 2181

WORKDIR /opt/zookeeper-3.4.6

CMD /bin/bash /opt/zookeeper-3.4.6/bin/zkServer.sh start-foreground

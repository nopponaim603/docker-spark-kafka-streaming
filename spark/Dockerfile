FROM ubuntu

# Environment
ENV SPARK_VERSION 3.3.0
ENV HADOOP_VERSION 3
ENV SCALA_VERSION 2.13
ENV SPARK_HOME /usr/local/spark
ENV HADOOP_HOME /usr/local/hadoop
# wget
RUN apt-get -y update && apt-get install -y wget


# Java
RUN apt-get install -y --no-install-recommends openjdk-8-jre-headless

# Hadoop
# https://dlcdn.apache.org/hadoop/common/hadoop-3.3.4/hadoop-3.3.4.tar.gz
# RUN cd /tmp && \
#    wget https://dlcdn.apache.org/hadoop/common/hadoop-3.3.4/hadoop-3.3.4.tar.gz && \
#    tar -xvzf https://dlcdn.apache.org/hadoop/common/hadoop-3.3.4/hadoop-3.3.4.tar.gz -C /usr/local && \
#    rm https://dlcdn.apache.org/hadoop/common/hadoop-3.3.4/hadoop-3.3.4.tar.gz

#RUN cd /usr/local && ln -s https://dlcdn.apache.org/hadoop/common/hadoop-3.3.4/hadoop-3.3.4.tar.gz hadoop

# Spark
# Old version
# http://d3kbcqa49mib13.cloudfront.net/spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION}.tgz
# current version
# https://dlcdn.apache.org/spark/spark-3.3.0/spark-3.3.0-bin-hadoop3-scala2.13.tgz
RUN cd /tmp && \
    wget https://dlcdn.apache.org/spark/spark-${SPARK_VERSION}/spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION}-scala${SCALA_VERSION}.tgz && \
    tar -xvzf spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION}-scala${SCALA_VERSION}.tgz -C /usr/local && \
    rm spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION}-scala${SCALA_VERSION}.tgz

RUN cd /usr/local && ln -s spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION}-scala${SCALA_VERSION} spark

# Spark Kafka Streaming
# Older
# wget http://repo1.maven.org/maven2/org/apache/spark/spark-streaming-kafka-0-10-assembly_${SCALA_VERSION}/${SPARK_VERSION}/spark-streaming-kafka-0-10-assembly_${SCALA_VERSION}-${SPARK_VERSION}.jar && \
# Current Version
# https://repo.mavenlibs.com/maven/org/apache/spark/spark-streaming-kafka-0-10-assembly_2.13/3.3.0/spark-streaming-kafka-0-10-assembly_2.13-3.3.0.jar?utm_source=mavenlibs.com
RUN cd /tmp && \
    wget https://repo.mavenlibs.com/maven/org/apache/spark/spark-streaming-kafka-0-10-assembly_${SCALA_VERSION}/${SPARK_VERSION}/spark-streaming-kafka-0-10-assembly_${SCALA_VERSION}-${SPARK_VERSION}.jar && \
    mv spark-streaming-kafka-0-10-assembly_${SCALA_VERSION}-${SPARK_VERSION}.jar /usr/local/spark/jars

EXPOSE 8080

EXPOSE 6066

EXPOSE 7077

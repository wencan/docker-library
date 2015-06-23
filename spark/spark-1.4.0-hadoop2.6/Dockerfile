FROM wencan/scala:2.11

MAINTAINER wencan <i@wencan.org>

ENV SPARK_VERSION 1.4.0
ENV HADOOP_VERSION 2.6

RUN wget http://www.apache.org/dist/spark/spark-$SPARK_VERSION/spark-$SPARK_VERSION-bin-hadoop$HADOOP_VERSION.tgz \
    && wget http://www.apache.org/dist/spark/spark-$SPARK_VERSION/spark-$SPARK_VERSION-bin-hadoop$HADOOP_VERSION.tgz.asc \
    && gpg --keyserver pgpkeys.mit.edu --recv-key FC8ED089 \
    && gpg --verify spark-$SPARK_VERSION-bin-hadoop$HADOOP_VERSION.tgz.asc spark-$SPARK_VERSION-bin-hadoop$HADOOP_VERSION.tgz \
    && tar xzf spark-$SPARK_VERSION-bin-hadoop$HADOOP_VERSION.tgz \
    && mkdir -p /opt/spark \
    && mv spark-$SPARK_VERSION-bin-hadoop$HADOOP_VERSION/* /opt/spark \
    && rm -rf spark-$SPARK_VERSION-bin-hadoop$HADOOP_VERSION \
            spark-$SPARK_VERSION-bin-hadoop$HADOOP_VERSION.tgz.asc \
            spark-$SPARK_VERSION-bin-hadoop$HADOOP_VERSION.tgz
            
ENV SPARK_HOME /opt/spark
ENV PATH $PATH:$SPARK_HOME/bin

CMD ["spark-shell"]

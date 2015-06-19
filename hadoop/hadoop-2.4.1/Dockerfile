FROM java:openjdk-7-jdk

MAINTAINER wencan <i@wencan.org>

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        build-essential libtool automake cmake maven zlib1g-dev libssl-dev pkg-config\
    && rm -rf /var/lib/apt/lists/*
    
ENV PROTOBUF_VERSION 2.5.0
RUN wget https://github.com/google/protobuf/releases/download/v2.5.0/protobuf-$PROTOBUF_VERSION.tar.gz \
    && tar xzf protobuf-$PROTOBUF_VERSION.tar.gz \
    && cd protobuf-$PROTOBUF_VERSION \
    && ./autogen.sh \
    && ./configure \
    && make \
    && make check \
    && make install \
    && cd ../ \
    && rm -rf protobuf-$PROTOBUF_VERSION.tar.gz protobuf-$PROTOBUF_VERSION \
    && ldconfig

ENV HADOOP_VERSION 2.4.1
RUN wget http://archive.apache.org/dist/hadoop/core/hadoop-$HADOOP_VERSION/hadoop-$HADOOP_VERSION-src.tar.gz \
    && wget http://archive.apache.org/dist/hadoop/core/hadoop-$HADOOP_VERSION/hadoop-$HADOOP_VERSION-src.tar.gz.asc \
    && gpg --keyserver pgpkeys.mit.edu --recv-key A210C095 \
    && gpg --verify hadoop-$HADOOP_VERSION-src.tar.gz.asc hadoop-$HADOOP_VERSION-src.tar.gz \
    && tar zxf hadoop-$HADOOP_VERSION-src.tar.gz \
    && cd hadoop-$HADOOP_VERSION-src \
    && mvn package -Pdist,native -DskipTests -Dtar \
    && tar xzf hadoop-dist/target/hadoop-$HADOOP_VERSION.tar.gz \
    && mv hadoop-$HADOOP_VERSION /opt/hadoop/ \
    && cd ../ \
    && rm -rf hadoop-$HADOOP_VERSION-src.tar.gz hadoop-$HADOOP_VERSION-src.tar.gz.asc hadoop-$HADOOP_VERSION-src

ENV JAVA_HOME /usr/lib/jvm/java-7-openjdk-amd64
ENV HADOOP_HOME /opt/hadoop
ENV PATH $PATH:$HADOOP_HOME/bin
    
CMD ["/opt/hadoop/bin/hadoop"]


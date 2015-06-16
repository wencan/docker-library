FROM java:openjdk-7u79-jdk

MAINTAINER wencan <i@wencan.org>

RUN apt-get update \
    && apt-get install -y --no-install-recommends build-essential libtool automake cmake maven \
    && rm -rf /var/lib/apt/lists/*

RUN wget https://github.com/google/protobuf/releases/download/v2.5.0/protobuf-2.5.0.tar.gz \
    && tar xzf protobuf-2.5.0.tar.gz \
    && cd protobuf-2.5.0 \
    && ./autogen.sh \
    && ./configure \
    && make \
    && make check \
    && make install \
    && cd ../ \
    && rm -rf protobuf-2.5.0.tar.gz protobuf-2.5.0 \
    && ldconfig

RUN wget http://archive.apache.org/dist/hadoop/core/hadoop-2.4.1/hadoop-2.4.1-src.tar.gz \
    && wget http://archive.apache.org/dist/hadoop/core/hadoop-2.4.1/hadoop-2.4.1-src.tar.gz.asc \
    && gpg --keyserver pgpkeys.mit.edu --recv-key A210C095 \
    && gpg --verify hadoop-2.4.1-src.tar.gz.asc hadoop-2.4.1-src.tar.gz \
    && tar zxf hadoop-2.4.1-src.tar.gz \
    && cd hadoop-2.4.1-src \
    && mvn package -Pdist,native -Dtar \
    && tar xzf hadoop-dist/target/hadoop-2.4.1.tar.gz \
    && mv hadoop-2.4.1 /opt/hadoop/
    && cd ../
    && rm -rf hadoop-2.4.1-src.tar.gz hadoop-2.4.1-src.tar.gz.asc hadoop-2.4.1-src
    
EXPORT HADOOP_HOME=/opt/hadoop
    
CMD ["/opt/hadoop/bin/hadoop"]


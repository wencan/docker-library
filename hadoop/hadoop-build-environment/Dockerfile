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


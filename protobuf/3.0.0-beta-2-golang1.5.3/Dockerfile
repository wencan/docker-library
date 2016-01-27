FROM golang:1.5.3

MAINTAINER wencan <i@wencan.org>

RUN apt-get update \
    && apt-get install -y --no-install-recommends autoconf automake libtool unzip \
    && rm -rf /var/lib/apt/lists/*

ENV PROTOBUF_VERSION 3.0.0-beta-2
RUN curl -L https://github.com/google/protobuf/archive/v$PROTOBUF_VERSION.tar.gz -o protobuf-$PROTOBUF_VERSION.tar.gz \
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

RUN go get -v github.com/golang/protobuf/protoc-gen-go 

WORKDIR /

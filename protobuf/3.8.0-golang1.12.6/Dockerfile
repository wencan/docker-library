FROM golang:1.12.6

MAINTAINER wencan <i@wencan.org>

RUN apt-get update \
    && apt-get install -y --no-install-recommends autoconf automake libtool \
    && rm -rf /var/lib/apt/lists/*

ENV PROTOBUF_VERSION 3.8.0
RUN curl -Ls https://github.com/protocolbuffers/protobuf/releases/download/v$PROTOBUF_VERSION/protobuf-all-$PROTOBUF_VERSION.tar.gz -o protobuf-all-$PROTOBUF_VERSION.tar.gz \
    && tar xzf protobuf-all-$PROTOBUF_VERSION.tar.gz \
    && cd protobuf-$PROTOBUF_VERSION \
    && ./autogen.sh \
    && ./configure \
    && make \
    && make check \
    && make install \
    && cd ../ \
    && rm -rf protobuf-all-$PROTOBUF_VERSION.tar.gz protobuf-$PROTOBUF_VERSION \
    && ldconfig

RUN go get -v github.com/golang/protobuf/protoc-gen-go

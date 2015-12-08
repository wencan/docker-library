FROM buildpack-deps:jessie

MAINTAINER wencan <i@wencan.org>

RUN apt-get update \
    && apt-get install -y --no-install-recommends unzip \
    && rm -rf /var/lib/apt/lists/*

ENV PROTOBUF_VERSION 3.0.0-beta-1
RUN curl -Ls https://github.com/google/protobuf/archive/v$PROTOBUF_VERSION.tar.gz -o protobuf-$PROTOBUF_VERSION.tar.gz \
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

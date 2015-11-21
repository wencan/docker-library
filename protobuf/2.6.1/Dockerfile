FROM buildpack-deps:jessie

MAINTAINER wencan <i@wencan.org>

ENV PROTOBUF_VERSION 2.6.1
RUN wget https://github.com/google/protobuf/releases/download/v$PROTOBUF_VERSION/protobuf-$PROTOBUF_VERSION.tar.gz \
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

FROM java:openjdk-7-jdk

MAINTAINER wencan <i@wencan.org>

ENV SCALA_VERSION 2.11.7
RUN wget http://downloads.typesafe.com/scala/$SCALA_VERSION/scala-$SCALA_VERSION.tgz \
        -O scala-$SCALA_VERSION.tgz \
    && tar xzf scala-$SCALA_VERSION.tgz \
    && mkdir -p /opt/scala \
    && mv scala-$SCALA_VERSION/* /opt/scala/ \
    && rm -rf scala-$SCALA_VERSION.tgz scala-$SCALA_VERSION

ENV SCALA_HOME /opt/scala
ENV PATH $PATH:$SCALA_HOME/bin

CMD ["scala"]


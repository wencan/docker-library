FROM buildpack-deps:jessie

MAINTAINER wencan <i@wencan.org>

RUN mkdir -p /opt/jdk
WORKDIR /opt/jdk
RUN wget --no-check-certificate --no-cookies --header "Cookie: oraclelicense=accept-securebackup-cookie" http://download.oracle.com/otn-pub/java/jdk/7u80-b15/jdk-7u80-linux-x64.tar.gz
RUN tar xzf jdk-7u80-linux-x64.tar.gz && mv jdk1.7.0_80/* ./ && rm -rf jdk1.7.0_80

RUN mkdir -p /usr/lib/jvm/ && ln -s  /opt/jdk /usr/lib/jvm/default-java

ENV JAVA_HOME /usr/lib/jvm/default-java
ENV PATH $PATH:$JAVA_HOME/bin

WORKDIR /root/

CMD ["java"]

FROM debian:jessie

MAINTAINER wencan <i@wencan.org>

RUN printf "deb http://httpredir.debian.org/debian jessie main contrib" > /etc/apt/sources.list
RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        wget java-package build-essential libgl1-mesa-glx libgtk2.0-0 libxslt1.1 libxtst6 libxxf86vm1 \
    && rm -rf /var/lib/apt/lists/*

RUN groupadd java && useradd -r -g java java

WORKDIR /tmp
RUN wget --no-check-certificate --no-cookies --header "Cookie: oraclelicense=accept-securebackup-cookie" \
        -O jdk-7u79-linux-x64.tar.gz \
        http://download.oracle.com/otn-pub/java/jdk/7u79-b15/jdk-7u79-linux-x64.tar.gz \
    && chmod +r jdk-7u79-linux-x64.tar.gz \
    && su java -c 'yes | fakeroot make-jpkg jdk-7u79-linux-x64.tar.gz' \
    && dpkg --install oracle-java7-jdk_7u79_amd64.deb \
    && rm jdk-7u79-linux-x64.tar.gz oracle-java7-jdk_7u79_amd64.deb

WORKDIR /

RUN ln -s /usr/lib/jvm/jdk-7-oracle-x64 /usr/lib/jvm/default-java
ENV JAVA_HOME /usr/lib/jvm/default-java

CMD ["java"]

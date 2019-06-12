FROM ubuntu:18.04

RUN apt-get update && apt-get install -y \
    jq \
    time \
    automake \
    build-essential \
    curl \
    ruby \
    ruby-dev \
    zlib1g-dev \
    git \
 && rm -rf /var/lib/apt/lists/*
RUN gem install fpm
RUN curl -fSsL -O https://github.com/oracle/graal/releases/download/vm-19.0.0/graalvm-ce-linux-amd64-19.0.0.tar.gz && \
    tar xf graalvm-ce-linux-amd64-19.0.0.tar.gz && \
    mkdir -p /opt/graalvm && \
    mv graalvm-ce-19.0.0 /opt/graalvm && \
    rm -rf graalvm-ce-linux-amd64-19.0.0.tar.gz

RUN ln -s /opt/graalvm/graalvm-ce-19.0.0 /opt/graalvm/current
RUN ln -s /opt/graalvm/graalvm-ce-19.0.0/bin/java /usr/bin/java
RUN ln -s /opt/graalvm/graalvm-ce-19.0.0/bin/javac /usr/bin/javac

RUN /opt/graalvm/graalvm-ce-19.0.0/bin/gu install native-image
RUN ln -s /opt/graalvm/graalvm-ce-19.0.0/bin/native-image /usr/bin/native-image

RUN curl -fSsL -O https://raw.githubusercontent.com/technomancy/leiningen/stable/bin/lein && \
    mv lein /usr/bin && \
    chmod a+x /usr/bin/lein

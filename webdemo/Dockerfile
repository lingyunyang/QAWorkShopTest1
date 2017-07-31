FROM ubuntu:16.04
MAINTAINER yali "yali@thoughtworks.com"

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && \
    apt-get install -y software-properties-common python-software-properties && \
    add-apt-repository -y ppa:openjdk-r/ppa && \
    apt-get install -y openjdk-8-jdk


ENV JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64


# Install curl
RUN apt-get -y install curl unzip

#gradle
RUN \
    cd /usr/local && \
    curl -L https://services.gradle.org/distributions/gradle-3.5-bin.zip -o gradle-3.5-bin.zip && \
    unzip gradle-3.5-bin.zip && \
    rm gradle-3.5-bin.zip


  
WORKDIR /src
COPY ./ /src  


ENV GRADLE_HOME=/usr/local/gradle-3.5
ENV PATH=$PATH:$GRADLE_HOME/bin
EXPOSE 80
CMD ["/bin/bash"]
FROM docker.io/fedora:27
MAINTAINER Grzegorz Grzybek <gr.grzybek@gmail.com>
RUN groupadd -g 22693 ggrzybek && useradd -u 22693 -g ggrzybek ggrzybek
RUN dnf install -y tar telnet unzip which wget procps-ng iproute net-tools && \
    dnf clean all -y
COPY jdk-8u202-linux-x64.tar.gz /home/ggrzybek/jdk-8u202-linux-x64.tar.gz 
RUN wget http://archive.apache.org/dist/maven/maven-3/3.6.0/binaries/apache-maven-3.6.0-bin.tar.gz -O /home/ggrzybek/apache-maven-3.6.0-bin.tar.gz
RUN mkdir /work
WORKDIR /home/ggrzybek
USER ggrzybek
RUN tar xf jdk-8u202-linux-x64.tar.gz
RUN tar xf apache-maven-3.6.0-bin.tar.gz

RUN echo 'JAVA_HOME=/home/ggrzybek/jdk1.8.0_202' >> .bashrc && \
    echo 'MAVEN_HOME=/home/ggrzybek/apache-maven-3.6.0' >> .bashrc && \
    echo 'MAVEN_OPTS="-Xmx3072m"' >> .bashrc && \
    echo 'PATH=$JAVA_HOME/bin:$MAVEN_HOME/bin:$PATH' >> .bashrc && \
    echo 'export PATH JAVA_HOME MAVEN_HOME MAVEN_OPTS' >> .bashrc
RUN rm jdk-8u202-linux-x64.tar.gz apache-maven-3.6.0-bin.tar.gz
WORKDIR /work
EXPOSE 8181 2181 8101 44444 1099 61616 5005 5006 5007

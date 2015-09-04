FROM docker.io/fedora:22
MAINTAINER Grzegorz Grzybek <gr.grzybek@gmail.com>
RUN groupadd -g 22693 ggrzybek && useradd -u 22693 -g ggrzybek ggrzybek
RUN dnf install -y tar telnet unzip which wget && \
    dnf clean all -y
RUN wget --header "Cookie: oraclelicense=accept-securebackup-cookie" http://download.oracle.com/otn-pub/java/jdk/8u60-b27/jdk-8u60-linux-x64.tar.gz -O /home/ggrzybek/jdk-8u60-linux-x64.tar.gz
RUN wget http://archive.apache.org/dist/maven/maven-3/3.3.3/binaries/apache-maven-3.3.3-bin.tar.gz -O /home/ggrzybek/apache-maven-3.3.3-bin.tar.gz
RUN mkdir /work
WORKDIR /home/ggrzybek
USER ggrzybek
RUN tar xf jdk-8u60-linux-x64.tar.gz
RUN tar xf apache-maven-3.3.3-bin.tar.gz

RUN echo 'JAVA_HOME=/home/ggrzybek/jdk1.8.0_60' >> .bashrc && \
    echo 'MAVEN_HOME=/home/ggrzybek/apache-maven-3.3.3' >> .bashrc && \
    echo 'MAVEN_OPTS="-Xmx3072m"' >> .bashrc && \
    echo 'PATH=$JAVA_HOME/bin:$MAVEN_HOME/bin:$PATH' >> .bashrc && \
    echo 'export PATH JAVA_HOME MAVEN_HOME MAVEN_OPTS' >> .bashrc
RUN rm jdk-8u60-linux-x64.tar.gz apache-maven-3.3.3-bin.tar.gz
WORKDIR /work
EXPOSE 8181 2181 8101 44444 1099 61616 5005 5006 5007

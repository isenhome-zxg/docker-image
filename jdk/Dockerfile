From centos:latest

RUN yum update && yum install -y wget
RUN wget --no-cookies --no-check-certificate --header "Cookie:gpw_e24=http%3a%2f%2fwww.oracle.com%2ftechnetwork%2fjava%2fjavase%2fdownloads%2fjdk8-downloads-2133151.html;oraclelicense=accept-securebackup-cookie" http://download.oracle.com/otn-pub/java/jdk/8u144-b01/090f390dda5b47b9b721c7dfaa008135/jdk-8u144-linux-x64.rpm
RUN rpm localinstall jdk-8u144-linux-x64.rpm
RUN rm -rf jdk-8u144-linux-x64.rpm

ENV JAVA_HOME=/usr/java/default
ENV PATH=$JAVA_HOME/bin:$PATH
ENV CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar

RUN source /etc/profile
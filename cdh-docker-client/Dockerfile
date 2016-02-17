FROM ubuntu:14.04
MAINTAINER David Greco "greco@acm.org"
RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -yq curl
 
#add CDH repo
RUN curl http://archive.cloudera.com/cdh5/ubuntu/trusty/amd64/cdh/archive.key | apt-key add -
RUN curl http://archive.cloudera.com/cdh5/ubuntu/trusty/amd64/cdh/cloudera.list > /etc/apt/sources.list.d/cloudera.list
 
# add CM repo 
RUN curl http://archive.cloudera.com/cm5/ubuntu/trusty/amd64/cm/archive.key | apt-key add -
RUN curl http://archive.cloudera.com/cm5/ubuntu/trusty/amd64/cm/cloudera.list > /etc/apt/sources.list.d/cloudera-manager.list
 
RUN apt-get update
RUN DEBIAN_FRONTEND=noninteractive apt-get install -yq oracle-j2sdk1.7
ENV JAVA_HOME /usr/lib/jvm/java-7-oracle-cloudera
ENV PATH $JAVA_HOME/bin:$PATH
 
RUN DEBIAN_FRONTEND=noninteractive apt-get install -yq oracle-j2sdk1.6 apt-transport-https ssh net-tools vim inetutils-ping cloudera-manager-agent

RUN echo 'root:root' | chpasswd 
RUN sed -e 's/without-password/yes/g' /etc/ssh/sshd_config > /etc/ssh/tmp; mv /etc/ssh/tmp /etc/ssh/sshd_config
RUN sed -e '88cUsePAM no' /etc/ssh/sshd_config > /etc/ssh/tmp; mv /etc/ssh/tmp /etc/ssh/sshd_config
RUN service ssh restart

ADD start.sh start.sh
ADD start_cdh.sh start_cdh.sh

# Ports for Cloudera Client
EXPOSE 22

ENTRYPOINT ["sh"]

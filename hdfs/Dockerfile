FROM docker-hadoop:1.0

MAINTAINER isenhome "84655709@qq.com"

RUN rpm -ivh http://dl.fedoraproject.org/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm
RUN yum install -y supervisor
RUN mkdir -p /var/log/supervisor
COPY supervisord-hdfs.conf /etc/supervisord.conf

EXPOSE 22

CMD ["/usr/bin/supervisord"]

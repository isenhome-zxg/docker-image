FROM centos-ssh-jdk:1.1

MAINTAINER isenhome "84655709@qq.com"

RUN yum update
# RUN rpm -ivh http://dl.fedoraproject.org/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm
RUN yum install -y epel-release
RUN yum install -y redis
RUN yum install -y supervisor

RUN mkdir -p /var/log/supervisor
COPY supervisord.conf /etc/supervisord.conf
COPY redis.conf /etc/redis.conf

EXPOSE 22 6379
CMD ["/usr/bin/supervisord"]

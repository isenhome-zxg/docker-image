FROM centos-ssh-jdk:1.1

MAINTAINER isenhome "84655709@qq.com"

RUN rpm -ivh http://dl.fedoraproject.org/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm  
RUN yum install -y openssh-server sudo mysql-server mysql supervisor  

RUN mkdir -p /var/log/supervisor
COPY supervisord.conf /etc/supervisord.conf

EXPOSE 22 3306
CMD ["/usr/bin/supervisord"]

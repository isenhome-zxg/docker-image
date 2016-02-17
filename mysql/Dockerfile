FROM insaneworks/centos

MAINTAINER isenhome "84655709@qq.com"

RUN rpm -ivh http://dl.fedoraproject.org/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm  
RUN yum install -y openssh-server sudo mysql-server mysql supervisor  
RUN /etc/init.d/mysqld start &&\
    mysql -e "grant all privileges on *.* to 'root'@'%' identified by 'root';"&&\
    mysql -e "grant all privileges on *.* to 'root'@'localhost' identified by 'root';"&&\
    mysql -u root -proot -e "show databases;"

RUN mkdir -p /var/log/supervisor
COPY supervisord.conf /etc/supervisord.conf

EXPOSE 3306
CMD ["/usr/bin/supervisord"]

FROM centos:7

COPY CentOS-CR.repo /etc/yum.repos.d/CentOS-CR.repo

RUN yum update -y \
    && yum install -y epel-release yum-utils \
    && yum clean all && rm -rf /var/cache/yum

FROM centos:7

USER root

RUN yum -y update && \
    yum install -y epel-release deltarpm && \
    yum install -y zsh wget ImageMagick vim htop cmake3 && \
    yum groupinstall -y "Development Tools" && \
    yum clean all && \
    localedef -i en_US -f UTF-8 en_US.UTF-8 && \
    ln -s /usr/bin/cmake3 usr/bin/cmake

CMD /bin/zsh

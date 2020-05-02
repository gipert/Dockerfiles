FROM gipert/centos-base:7

ARG ROOT_VERSION="6.20.02"

USER root
WORKDIR /tmp

COPY packages /packages

RUN yum install -y $(cat /packages) && \
    yum clean all && \
    rm /packages

RUN mkdir -p /opt/root && \
    wget -q -O- "https://root.cern/download/root_v${ROOT_VERSION}.Linux-centos7-x86_64-gcc4.8.tar.gz" \
    | tar --strip-components 1 -xz -C "/opt/root"

ENV ROOTSYS="/ot/root" \
    PATH="/opt/root/bin:$PATH" \
    LD_LIBRARY_PATH="/opt/root/lib:$LD_LIBRARY_PATH" \
    MANPATH="/opt/root/man:$MANPATH" \
    PYTHONPATH="/opt/root/lib:$PYTHONPATH"

WORKDIR /data
CMD /opt/root/bin/root

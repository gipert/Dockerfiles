FROM gipert/root-cern:6.20.02

ARG BAT_VERSION="1.0.0"

USER root

WORKDIR /opt
RUN mkdir -p /opt/bat/src && \
    wget -q -O- "https://github.com/bat/bat/releases/download/v${BAT_VERSION}/BAT-${BAT_VERSION}.tar.gz" \
    | tar --strip-components 1 -xz -C "/opt/bat/src" && cd /opt/bat/src && \
    ./configure \
        --with-rootsys="/opt/root" \
        --with-cuba=download \
        --enable-parallel \
        --prefix=/opt/bat && \
    make -j"$(nproc)" && make install

ENV PATH="$PATH:/opt/bat/bin" \
    LD_LIBRARY_PATH="$LD_LIBRARY_PATH:/usr/lib64:/opt/bat/lib"

WORKDIR /data
CMD bat-config

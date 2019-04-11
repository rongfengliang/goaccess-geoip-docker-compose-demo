# Builds a goaccess image from the current working directory:
FROM alpine:edge

WORKDIR /goaccess

RUN wget https://tar.goaccess.io/goaccess-1.3.tar.gz

RUN tar -xzvf goaccess-1.3.tar.gz

RUN cd goaccess-1.3/

ARG build_deps="build-base ncurses-dev autoconf automake git gettext-dev"
ARG runtime_deps="tini ncurses libintl gettext openssl-dev"

RUN apk update && \
    apk add -u $runtime_deps $build_deps  geoip-dev && \
    wget -O goaccess-1.3.tar.gz  https://tar.goaccess.io/goaccess-1.3.tar.gz && \
    tar -xzvf goaccess-1.3.tar.gz && \
    cd goaccess-1.3 && \
    autoreconf -fiv && \
    ./configure --enable-utf8 --enable-geoip=legacy  --with-openssl && \
    make && \
    make install && \
    apk del $build_deps && \
    rm -rf /var/cache/apk/* /tmp/goaccess/* /goaccess

VOLUME /srv/data
VOLUME /srv/logs
VOLUME /srv/report
EXPOSE 7890

ENTRYPOINT ["/sbin/tini", "--"]
CMD ["goaccess", "--no-global-config", "--config-file=/srv/data/goaccess.conf"]
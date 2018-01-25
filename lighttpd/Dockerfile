FROM debian:7.11-slim
#MAINTAINER UmVnaXN0ZXIgcmVnaXN0ZXJkZWRpY2F0ZWQrZG9ja2VyKGF0KWdtYWlsLmNvbQo=

ENV UID     100
ENV GID     101

RUN set -ex && \
    apt-get add --no-cache lighttpd &&\
    apt-get -y clean &&\
    rm -rf /var/lib/apt/lists/*

COPY entrypoint.sh /usr/bin/entrypoint.sh
COPY lighttpd.conf /etc/lighttpd/lighttpd.conf
COPY index.html /var/www/index.html

WORKDIR /var/www

VOLUME ["/var/www"]

EXPOSE 80

ENTRYPOINT ["/usr/bin/entrypoint.sh"]

CMD ["lighttpd", "-D", "-f", "/etc/lighttpd/lighttpd.conf"]

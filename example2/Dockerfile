FROM debian:stretch

LABEL VERSION="1.0"
LABEL MAINTAINER="philippe.bouamriou@thalesgroup.com"

RUN set -x \
    && apt-get update \
    && apt-get install --no-install-recommends --no-install-suggests \
       -y lighttpd

EXPOSE 80
COPY lighttpd.conf /
COPY index.html /var/www
ENTRYPOINT [ "lighttpd", "-D" , "-f", "/lighttpd.conf"]
STOPSIGNAL SIGQUIT
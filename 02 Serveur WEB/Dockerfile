FROM debian:stretch

LABEL VERSION="1.0"
LABEL MAINTAINER="philippe.bouamriou@thalesgroup.com"

RUN set -x \
    && apt-get update \
    && apt-get install --no-install-recommends --no-install-suggests \
       -y lighttpd curl

EXPOSE 80
COPY lighttpd.conf /
COPY index.html /var/www
ENTRYPOINT [ "lighttpd", "-D" , "-f", "/lighttpd.conf"]
HEALTHCHECK --interval=10s --timeout=3s \
  CMD curl -f http://localhost/ || exit 1
STOPSIGNAL SIGQUIT
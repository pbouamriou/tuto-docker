FROM debian:stretch

LABEL MAINTAINER="philippe.bouamriou@thalesgroup.com"
LABEL VERSION="1.0"

RUN set -x \
    && apt-get update \
    && apt-get install --no-install-recommends --no-install-suggests \
       -y procps

ENTRYPOINT ["/usr/bin/top", "-b"]
CMD [ "-c" ]
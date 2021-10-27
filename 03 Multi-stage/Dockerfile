FROM debian:stretch as DEV

LABEL VERSION="1.0"
LABEL MAINTAINER="philippe.bouamriou@thalesgroup.com"

RUN set -x \
    && apt-get update \
    && apt-get install --no-install-recommends --no-install-suggests \
       -y build-essential

WORKDIR /tmp
COPY hello.c ./
RUN gcc -o hello hello.c

FROM debian:stretch as OPS
LABEL VERSION="1.0"
LABEL MAINTAINER="philippe.bouamriou@thalesgroup.com"

WORKDIR /root

COPY --from=DEV /tmp/hello ./
CMD ["./hello"]



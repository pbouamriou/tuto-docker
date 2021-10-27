FROM ghcr.io/linuxserver/code-server

LABEL MAINTAINER="pbouamriou@me.com"

RUN apt-get update && \
    apt-get install -y \
       zsh \
       build-essential \
       gcc-8 \
       g++-8 \
       make \
    && update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-8 8 \
    && update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-8 8
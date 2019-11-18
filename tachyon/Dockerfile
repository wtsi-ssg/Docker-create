FROM ubuntu:bionic

RUN apt-get update 
RUN apt-get -qq -y upgrade

RUN apt-get install -qq -y apt-utils automake \
    build-essential \
    curl cmake \
    git libssl-dev \
    autoconf automake \
    libcurl4-gnutls-dev \
    libgsl-dev libgsl23 \
    libncurses5 libncurses5-dev libperl-dev \
    libssl-dev libtool liblzma-dev libbz2-dev \
    linux-libc-dev \
    zlib1g-dev sudo

RUN apt-get autoclean

RUN git clone --recursive https://github.com/mklarqvist/tachyon && \
    cd tachyon && \
    ./install.sh 

RUN useradd -ms /bin/bash dev
USER dev
WORKDIR /home/dev

ENV LD_LIBRARY_PATH=/usr/local/lib:$LD_LIBRARY_PATH \
    PATH=/tachyon:$PATH

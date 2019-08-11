FROM ubuntu:18.04

ENV DEBIAN_FRONTED=noninteractive

RUN apt-get update 
RUN apt-get -y upgrade

RUN apt-get install -y apt-utils autoconf automake autotools-dev \
    build-essential \
    git \
    libbz2-dev libcurl4-gnutls-dev libgsl-dev libgsl23 \
    liblzma-dev libncurses5 libncurses5-dev \
    libperl-dev libssl-dev libtool \
    linux-libc-dev \
    zlib1g-dev

RUN git clone https://github.com/lh3/bwa.git && \
    cd bwa && \
    make && \
    cp bwa /usr/local/bin/ 

RUN apt-get autoclean

RUN rm -rf bwa

RUN useradd -ms /bin/bash dev
USER dev
WORKDIR /home/dev

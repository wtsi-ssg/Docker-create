FROM ubuntu:18.04

ENV DEBIAN_FRONTED=noninteractive

RUN apt-get update && \
    apt-get -y upgrade

RUN apt-get install -qq -y \ 
    autoconf automake autotools-dev \
    build-essential \
    git \
    libcurl4-gnutls-dev \
    libgsl-dev libgsl23 \
    libncurses5 libncurses5-dev libperl-dev \
    libssl-dev libtool liblzma-dev libbz2-dev \
    linux-libc-dev \
    zlib1g-dev

RUN git clone https://github.com/samtools/htslib.git && \
    cd htslib && \
    autoheader && \
    autoconf && \
    ./configure && \
    make && \
    make install && \
    cd ..

RUN git clone https://github.com/samtools/bcftools.git && \
    cd bcftools && \
    autoheader && autoconf && ./configure --enable-libgsl --enable-perl-filters && \
    make && \
    cd ..

RUN git clone https://github.com/samtools/samtools.git && \
    cd samtools && \
    autoheader && autoconf && ./configure && \
    make && \
    make install

RUN apt-get autoclean && \
    rm -rf samtools && \
    rm -rf bcftools && \
    rm -rf htslib

RUN useradd -ms /bin/bash dev
USER dev
WORKDIR /home/dev


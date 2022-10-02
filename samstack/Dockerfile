FROM ubuntu:20.04

LABEL version=’0.1.0’ \
    description='samstack toolset for insformatics workflows' \
    maintainer='peter.clapham@sanger.ac.uk'

ENV DEBIAN_FRONTED=noninteractive

RUN apt-get update
RUN apt-get -y upgrade
 
RUN apt-get install -qq -y \ 
    autoconf automake autotools-dev \
    build-essential \
    git \
    libcurl4-gnutls-dev \
    libncurses5 libncurses5-dev libperl-dev \
    libgsl-dev libgsl23 \
    libssl-dev libtool liblzma-dev libbz2-dev \
    linux-libc-dev \
    zlib1g-dev

RUN git clone https://github.com/samtools/htslib.git && \
    cd htslib && \
    git submodule update --init --recursive && \
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


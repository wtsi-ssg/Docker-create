FROM ubuntu:bionic

RUN apt-get update && \
    apt-get -qq -y upgrade

RUN apt-get install -qq -y apt-utils automake \
    bc bison build-essential \
    curl cmake \
    flex \
    gawk git \
    jq \
    libbz2-dev libcairo2 libffi-dev liblz4-dev \
    liblzma-dev libjansson-dev libncurses-dev \
    libprotoc-dev librdf-dev libtool lzma lzma-dev \
    pkg-config protobuf-compiler python-cairo \
    redland-utils rs \
    sudo \
    unzip 

RUN apt-get autoclean

COPY files/sudoers /etc/sudoers

RUN useradd -ms /bin/bash dev
USER dev
WORKDIR /home/dev

RUN  git clone --recursive https://github.com/vgteam/vg.git && \
     cd vg && \
     make get-deps && \
     . ./source_me.sh && make

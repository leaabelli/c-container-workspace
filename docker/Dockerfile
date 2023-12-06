FROM ubuntu:22.04 as dev

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && \
    apt-get dist-upgrade -y && \
    apt-get install -y --no-install-recommends \
        bundler \
        bzip2 \
        build-essential \
        git \
        gpg-agent \
        gosu \
        lsb-release \
        lcov \
        ninja-build \
        nano \
        python-is-python3 \
        python3 \
        python3-pip \
        software-properties-common \
        sudo \
        vagrant \
        wget \
        xz-utils && \
    python3 -m pip install --upgrade pip && \
    gem install bundler

ENV DEBIAN_FRONTEND=

RUN adduser --disabled-password --gecos "" user && \
    usermod -aG sudo user && \
    passwd -d user

ENV NOTVISIBLE="in users profile"
RUN echo "export VISIBLE=now" >> "/etc/profile"

RUN echo "\nexport USER=user" >> "/home/user/.bashrc"

VOLUME [ "/src" ]

WORKDIR /src

USER user

ENTRYPOINT [ "bash" ]

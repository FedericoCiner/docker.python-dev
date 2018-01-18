# python3-base Dockerfile

FROM federicociner/ubuntu:xenial
MAINTAINER Federico Ciner <federico.ciner@gmail.com>

ARG DEBIAN_FRONTEND=noninteractive

ENV LC_ALL en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LC_CTYPE en_US.UTF-8

COPY . /tmp/

RUN \
  apt-get update && \
  apt-get install -y --no-install-recommends \
    ed \
    locales \
    wget \
    ca-certificates \
    apt-transport-https \
    build-essential \
    curl \
    python3 \
    python3-dev \
    python3-pip \
    python3-matplotlib \
    python3-setuptools \
    python3-wheel \
    && echo "en_US.UTF-8 UTF-8" >> /etc/locale.gen && \
    locale-gen en_US.utf8 && \
    update-locale LANG=en_US.UTF-8 && \
    pip3 install --upgrade pip && \
    pip3 install -r /tmp/requirements.txt && \
  rm -rf /var/lib/apt/lists/*
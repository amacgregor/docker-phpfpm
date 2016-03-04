FROM ubuntu:15.04
MAINTAINER Allan MacGregor <amacgregor@allanmacgregor.com>

RUN apt-get update && apt-get install -y \
    wget \
    build-essential \
    bison \
    openssl \
    git-core \
    zlib1g \
    zlib1g-dev \
    automake \
    gcc \
    sqlite3 \
    autoconf \
    pkg-config \
    libssl-dev \
    libxml2-dev \
    libxslt-dev \
    libreadline5 \
    libreadline-dev \
    libreadline-dev \
    libsqlite3-0 \
    libsqlite3-dev \
    libssl-dev \
    libsslcommon2-dev \
    libcurl4-openssl-dev \
    libbz2-dev \
    libjpeg-dev \
    libpng-dev \
    libfreetype6-dev \
    libxpm-dev \
    libmcrypt-dev \
    libltdl-dev \
    libmhash-dev \
    supervisor \
    libmysqlclient-dev

# Download a copy of cweiske/phpfarm repo
RUN git clone https://github.com/amacgregor/phpfarm.git /opt/phpfarm

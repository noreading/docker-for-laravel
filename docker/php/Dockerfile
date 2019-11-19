FROM php:7.3-fpm

# Update package list
RUN apt-get update

# Install additional packages and PHP Extensions
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y --fix-missing \
        apt-utils \
        gnupg \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng-dev \
        libbz2-dev \
        libc6-dev \
        libmemcached-dev \
        libsasl2-dev \
        zlib1g-dev \
        zlib1g-dev \
        libzip-dev \
        libxml2-dev \
        g++ \
        openssl \
        libcurl4-gnutls-dev \
        uuid-dev \
        rsync \
        libzip-dev

RUN apt-get update
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y zip
RUN docker-php-ext-install bcmath mysqli pdo_mysql intl zip
RUN pecl install redis mongodb uuid
RUN docker-php-ext-enable redis mongodb uuid

# Cleanup packages
RUN apt-get auto-remove -y
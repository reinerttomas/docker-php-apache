FROM php:8.0-apache

RUN apt-get update \
    && apt-get -y --no-install-recommends install unzip

# https://github.com/mlocati/docker-php-extension-installer
ADD https://github.com/mlocati/docker-php-extension-installer/releases/latest/download/install-php-extensions /usr/local/bin/
RUN chmod +x /usr/local/bin/install-php-extensions && sync

RUN install-php-extensions @composer \
    pdo \
    pdo_mysql \
    mysqli \
    intl \
    zip

# Clear
RUN rm -rf /var/lib/apt/lists/*

WORKDIR /var/www/html
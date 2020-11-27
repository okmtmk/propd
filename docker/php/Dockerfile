FROM php:7.4-apache

RUN apt-get -y update \
    && apt-get install -y libzip-dev zlib1g-dev vim \
    apt-utils apt-transport-https libpcre3 \
    libpcre3-dev ca-certificates curl unzip default-mysql-client gnupg

RUN docker-php-ext-install pdo_mysql mysqli zip

COPY --from=composer /usr/bin/composer /usr/bin/composer

RUN composer global require "laravel/installer"

COPY php.ini /usr/local/etc/php/
COPY apache.conf /etc/apache2/sites-enabled/000-default.conf
RUN a2enmod rewrite

RUN curl -sL https://deb.nodesource.com/setup_12.x | bash -
RUN apt-get install -y nodejs

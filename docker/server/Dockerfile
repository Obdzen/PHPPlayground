FROM php:8.2-apache

RUN apt-get update \
    && apt-get upgrade -y \
    && apt-get install -y git unzip libzip-dev openssh-client \
    && apt-get install -y libpng-dev libjpeg62-turbo-dev libfreetype-dev \
    && apt-get install -y libpq-dev

RUN pecl install xdebug

RUN docker-php-ext-configure pgsql -with-pgsql=/usr/local/pgsql
RUN docker-php-ext-configure gd --with-freetype --with-jpeg

RUN docker-php-ext-install -j$(nproc) gd
RUN docker-php-ext-install pdo pdo_pgsql

WORKDIR /var/www/html/
USER www-data
FROM php:8.1-fpm

# Install Composer (including ZIP for Composer)
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN apt-get update && apt-get install -y \
libfreetype6-dev \
libjpeg62-turbo-dev \
libxslt-dev \
libicu-dev \
libmcrypt-dev \
libpng-dev \
libxml2-dev \
git \
libzip-dev \
libonig-dev

RUN docker-php-ext-install -j$(nproc) mysqli

RUN pecl install xdebug \
    && docker-php-ext-enable xdebug

# Вычищаем пакеты apt
RUN apt-get -y autoremove
RUN apt-get clean
RUN rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

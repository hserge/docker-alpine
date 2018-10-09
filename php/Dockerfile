FROM php:7.2-fpm-alpine

RUN apk add --no-cache $PHPIZE_DEPS \
    # pgsql
    postgresql-dev \
    # gd
    freetype-dev \
    libjpeg-turbo-dev \
    libmcrypt-dev \
    libpng-dev \
    # xdebug
    && pecl install xdebug-2.6.1 \
    && docker-php-ext-enable xdebug \
    # pgsql
    && docker-php-ext-install pdo pdo_pgsql \
    # gd
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j"$(getconf _NPROCESSORS_ONLN)" gd

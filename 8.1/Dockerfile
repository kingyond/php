FROM php:8-fpm-alpine

RUN docker-php-source extract \
#    && sed -i 's/dl-cdn.alpinelinux.org/mirrors.aliyun.com/' /etc/apk/repositories \
    && apk update \
    && apk upgrade
RUN apk add --no-cache bash \
    && apk --update add wget curl curl-dev git zip openssl oniguruma-dev pcre-dev zlib-dev libpng-dev libjpeg-turbo-dev \
    postgresql-dev imagemagick-dev postgresql-dev libxml2-dev libmcrypt-dev autoconf g++ libtool make linux-headers
RUN docker-php-ext-install pdo pdo_mysql mysqli mbstring bcmath gd
RUN pecl install imagick \
    && docker-php-ext-enable imagick
RUN pecl install redis \
    && docker-php-ext-enable redis
RUN docker-php-source delete \

RUN rm /var/cache/apk/* \
    && rm -rf /usr/src/php
RUN chown -R www-data:www-data /var/www


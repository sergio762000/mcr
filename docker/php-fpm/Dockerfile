FROM php:8.2-fpm
LABEL authors="SGolovanov"

RUN apt-get update && apt-get install -y \
    libzip-dev \
    libssl-dev \
    && docker-php-ext-install -j$(nproc) zip pdo pdo_mysql

COPY ./php-custom.ini /usr/local/etc/php/conf.d/php-custom.ini

WORKDIR /var/www/mcr

VOLUME /var/www/mcr

CMD ["php-fpm"]
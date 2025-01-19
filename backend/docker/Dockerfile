ARG BASE_TAG=8.3.3-fpm-bullseye

FROM php:$BASE_TAG

RUN apt update && apt install -y nginx libonig-dev libxml2-dev supervisor git unzip wget libcurl4-openssl-dev pkg-config libssl-dev linux-libc-dev=5.10.209-2

RUN rm -f /var/log/nginx/access.log && \
    rm -f /var/log/nginx/error.log && \
    ln -s /dev/stdout /var/log/nginx/error.log && \
    ln -s /dev/stdout /var/log/nginx/access.log


RUN docker-php-ext-install bcmath ctype mbstring pdo pdo_mysql xml pcntl sockets

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" && \
    php composer-setup.php --quiet && \
    rm composer-setup.php && \
    mv composer.phar /usr/local/bin/composer

RUN docker-php-ext-install soap \
    && pecl install mongodb-1.15.0 \
    && docker-php-ext-enable mongodb

WORKDIR /var/www/html

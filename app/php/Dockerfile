FROM php:7.4-fpm

RUN cp /usr/local/etc/php/php.ini-production /usr/local/etc/php/php.ini \
    && docker-php-ext-install pdo_mysql \
    && docker-php-ext-install bcmath
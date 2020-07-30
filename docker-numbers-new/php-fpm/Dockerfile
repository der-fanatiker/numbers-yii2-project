FROM php:7.4-fpm

RUN apt-get update -y
RUN apt-get install -y libpng-dev libfreetype6-dev libjpeg62-turbo-dev
RUN docker-php-ext-install pdo_mysql
RUN pecl install xdebug && docker-php-ext-enable xdebug

RUN docker-php-ext-install -j$(nproc) iconv \
    && docker-php-ext-configure gd --with-freetype=/usr/include/ --with-jpeg=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd

COPY conf.d/docker.ini $PHP_INI_DIR/conf.d/
COPY conf.d/php.ini $PHP_INI_DIR/conf.d/

RUN usermod -u 1000 www-data
RUN usermod -G staff www-data

CMD ["php-fpm"]

EXPOSE 9000
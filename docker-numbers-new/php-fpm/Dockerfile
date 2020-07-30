FROM php:7.4-fpm

RUN apt-get update -y && apt-get install -y libpng-dev && docker-php-ext-install pdo_mysql gd
RUN pecl install xdebug && docker-php-ext-enable xdebug

COPY conf.d/docker.ini $PHP_INI_DIR/conf.d/
COPY conf.d/php.ini $PHP_INI_DIR/conf.d/

RUN usermod -u 1000 www-data
RUN usermod -G staff www-data

CMD ["php-fpm"]

EXPOSE 9000
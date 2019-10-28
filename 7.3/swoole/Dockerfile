#Use PHP 7.3 docker image with Apache on Debian Stretch
FROM php:7.3-cli-stretch

EXPOSE 80

# install some additional software and PHP extensions (both code and pecl ones)
# iconv, pdo, pdo_mysql are already available
#enable apache mod_rewrite
RUN apt-get update \
    && apt-get install -y mc git libfreetype6-dev libjpeg62-turbo-dev libpng-dev libxml2-dev unixodbc-dev libmcrypt-dev gnupg inetutils-ping dnsutils telnet screen libzip-dev \
    && docker-php-ext-install -j$(nproc) mysqli \
    && docker-php-ext-install -j$(nproc) pdo_mysql \
    && docker-php-ext-install -j$(nproc) opcache \
    && pecl install redis-4.3.0 \
    && pecl install mongodb \
    && pecl install swoole \
    && docker-php-ext-enable redis \
    && docker-php-ext-enable mongodb \
    && docker-php-ext-enable swoole

# install composer
RUN cd /root && php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" && php ./composer-setup.php && cp ./composer.phar /usr/bin/composer && rm ./composer-setup.php





FROM php:7.2-apache

RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng-dev \
        libxml2-dev \
        graphviz \
    && apt-get clean -y \
    && pecl install mcrypt-1.0.2 \
    && docker-php-ext-enable mcrypt \
    && docker-php-ext-install -j$(nproc) iconv \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd

RUN docker-php-ext-install mysqli xml zip mbstring

RUN pecl install xdebug-2.7.0 \
	&& docker-php-ext-enable xdebug \
    && pecl install xhprof \
    && mkdir -m a=rwx -p /var/log/xhprof \
    && umask 0022

RUN a2enmod rewrite

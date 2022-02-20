FROM php:7.2-apache

RUN apt-get update && apt-get install -y \
        libfreetype6-dev libjpeg62-turbo-dev libmcrypt-dev libpng-dev libxml2-dev libpq-dev \
        graphviz openssl curl vim wget unzip bc zip mc htop tmux \
        sysstat apg iotop \
        git subversion redis-tools \
        imagemagick wkhtmltopdf sendmail libssl-dev build-essential ffmpeg \
    && apt-get clean -y \
    && rm -rf /var/lib/apt/lists/* \
    && pecl install mcrypt-1.0.2 \
    && docker-php-ext-enable mcrypt \
    && docker-php-ext-install -j$(nproc) iconv \
    && docker-php-ext-install -j$(nproc) exif \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-configure pgsql -with-pgsql=/var/local/pgsql \
    && docker-php-ext-install -j$(nproc) gd

RUN docker-php-ext-install mysqli pdo pdo_mysql pdo_pgsql xml zip mbstring soap

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
RUN curl -sS https://psysh.org/psysh -o /usr/local/bin/psysh && chmod +x /usr/local/bin/psysh

RUN pecl install xdebug-2.7.0 \
	&& docker-php-ext-enable xdebug \
    && pecl install xhprof \
    && mkdir -m a=rwx -p /var/log/xhprof \
    && umask 0022

RUN a2enmod rewrite

WORKDIR /var/www/html

FROM php:7.3-fpm
MAINTAINER Sven Stam <sven@legalthings.io>

RUN apt-get update && apt-get install -y \
        libssl-dev \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng-dev \
        libzip-dev \
        zlib1g-dev \
        libicu-dev \
        g++ \
        libbase58-dev \
        locales \
        locales-all \
        libyaml-dev \
    && curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer \
    && docker-php-ext-install -j$(nproc) mbstring \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd \
    && docker-php-ext-configure intl \
    && docker-php-ext-install intl gettext zip bcmath

RUN locale-gen

RUN pecl install mongodb yaml base58-0.1.3 && docker-php-ext-enable mongodb yaml base58

RUN mkdir -p /app && rm -fr /var/www/html && ln -s /app /var/www/html
ADD sample/ /app

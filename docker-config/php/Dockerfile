FROM php:8.0-apache

# install composer
RUN cd /usr/bin && curl -s http://getcomposer.org/installer | php && ln -s /usr/bin/composer.phar /usr/bin/composer
RUN apt-get update \
&& apt-get install -y \
git \
zip \
unzip \
vim \
nodejs \
npm \
libpq-dev \
libzip-dev \
libgmp-dev \
ffmpeg \
&& apt clean \
&& rm -rf /var/lib/apt/lists/*

RUN docker-php-ext-install pdo_mysql pdo_pgsql mysqli zip gmp

RUN apt-get install --reinstall ca-certificates

RUN a2enmod rewrite
RUN a2enmod ssl

# xdebug install
RUN pecl install xdebug-3.1.6 && docker-php-ext-enable xdebug
COPY docker-php-ext-xdebug.ini /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini

WORKDIR /var/www/html

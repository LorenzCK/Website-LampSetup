FROM php:7.3.16-apache

RUN apt update && apt install -y \
    libcurl4>=7.44.0 \
    libcurl4-openssl-dev>=7.64.0 \
    libfreetype6-dev>=2.9.1 \
    libicu-dev>=63.1 \
    libjpeg62-turbo-dev>=1:1.5.2 \
    libmcrypt-dev>=2.5.8 \
    libxml++2.6-dev>=2.40.1 \
    libpng-dev>=1.6.36 \
    libxslt1-dev>=1.1.32 \
    libzip-dev>=1.5.1 \
    unzip>=6.0 \
 && rm -rf /var/lib/apt/lists/* \
 && apt-get clean -y

RUN docker-php-ext-configure gd --with-jpeg-dir=/usr/lib64/ --with-freetype-dir=/usr/lib64/ \
 && docker-php-ext-install gd

RUN docker-php-ext-install bcmath intl pdo_mysql soap sockets xsl zip

RUN cd /tmp && curl -sS https://getcomposer.org/installer | php && mv composer.phar /usr/local/bin/composer

COPY php.ini /usr/local/etc/php/php.ini

USER root

FROM php:8.1-fpm

#Instalaçao XDEBUG
RUN pecl install xdebug && docker-php-ext-enable xdebug

# Instalação do Composer
RUN apt-get update && apt-get install -y --no-install-recommends \
    wget \
    unzip \
    && rm -rf /var/lib/apt/lists/*

RUN wget https://getcomposer.org/installer -O composer-setup.php \
    && php composer-setup.php --install-dir=/usr/local/bin --filename=composer \
    && rm composer-setup.php

# # Dependências PHP
RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng-dev \
        libxml2-dev libxslt1-dev python-dev-is-python3 \
        curl unzip zip libzip-dev \
        libmcrypt-dev libreadline-dev

# # Instalação das extensões do PHP
RUN docker-php-ext-install -j$(nproc) \
    pdo_mysql \
    bcmath  \
    ctype \
    fileinfo \
    xml
    

#Configuração xdebug
RUN echo "xdebug.mode=debug" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini
RUN echo "xdebug.client_host=${XDEBUG_HOST}" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini
RUN echo "xdebug.client_port=${XDEBUG_PORT}" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini
#Fim Config XDEBUG

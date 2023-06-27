FROM php:8.2-fpm

#Extensões PHP
RUN docker-php-ext-install pdo_mysql

# Instalação das extensões do PHP
RUN apt-get update && apt-get install -y \
    libbz2-dev \
    libicu-dev \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libpng-dev \
    libssl-dev \
    libxml2-dev \
    zlib1g-dev \
    && docker-php-ext-install -j$(nproc) \
    pdo_mysql \
    bcmath \
    ctype \
    fileinfo \
    json \
    mbstring \
    openssl \
    tokenizer \
    xml

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

#Configuração xdebug
RUN echo "xdebug.mode=debug" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini
RUN echo "xdebug.client_host=${XDEBUG_HOST}" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini
RUN echo "xdebug.client_port=${XDEBUG_PORT}" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini
#Fim Config XDEBUG

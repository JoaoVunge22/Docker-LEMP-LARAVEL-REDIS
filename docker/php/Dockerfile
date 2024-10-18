FROM php:8.3.12-fpm-bullseye

## Diretório da aplicação
ARG APP_DIR=/var/www/app

## apt-utils é um extensão de recursos do gerenciador de pacotes APT
#RUN apt-get update -y && apt-get install -y --no-install-recommends \ apt-utils

## dependências recomendadas de desenvolvido para ambiente linux
RUN apt-get update && apt-get install -y \
    zlib1g-dev \
    libzip-dev \
    unzip \
    libpng-dev \
    libpq-dev \
    libxml2-dev

#Instalar Extensão
RUN docker-php-ext-install mysqli pdo pdo_mysql pdo_pgsql pgsql session xml
#RUN docker-php-ext-install redis
RUN docker-php-ext-install zip iconv simplexml pcntl gd fileinfo
#Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
RUN apt-get update -y

WORKDIR $APP_DIR
RUN cd $APP_DIR
RUN chown www-data:www-data $APP_DIR

RUN rm -rf vendor
#RUN composer update
RUN apt update -y && apt install nano git -y

EXPOSE 9000
#CMD ["php-pfm"]
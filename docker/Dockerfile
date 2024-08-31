# Usar la imagen base de PHP con Apache
FROM php:8.3-apache

RUN apt-get update && apt-get install -y \
libicu-dev \
libmariadb-dev \
unzip zip \
zlib1g-dev \
libpng-dev \
libfreetype6-dev \
libjpeg62-turbo-dev \
nano \
libpng-dev \
&& docker-php-ext-configure gd --with-freetype --with-jpeg \
&& docker-php-ext-install gd pdo pdo_mysql

RUN docker-php-ext-install gettext intl pdo_mysql gd

RUN docker-php-ext-configure gd --enable-gd --with-freetype --with-jpeg 

RUN a2enmod rewrite

COPY ./vhost.conf /etc/apache2/sites-available/000-default.conf

COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

WORKDIR /var/www/html

RUN chown -R www-data:www-data /var/www/html/ \
    && chmod -R 755 /var/www/html/


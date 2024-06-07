FROM php:7.4-apache

RUN apt-get update && \
    apt-get install -y libpng-dev libjpeg-dev libfreetype6-dev && \
    docker-php-ext-configure gd --with-freetype --with-jpeg && \
    docker-php-ext-install gd && \
    docker-php-ext-install mysqli pdo pdo_mysql && \
    docker-php-ext-enable mysqli pdo pdo_mysql && \
    docker-php-ext-install calendar

# Copiar archivo de configuración de Apache
COPY ./000-default.conf /etc/apache2/sites-available/000-default.conf

# Habilitar el módulo de reescritura de Apache
RUN a2enmod rewrite

# Instalar Node.js 10
RUN curl -sL https://deb.nodesource.com/setup_10.x | bash - \
    && apt-get install -y nodejs

# Instalar Composer
# COPY --from=composer:latest /usr/bin/composer /usr/bin/composer
RUN curl -sS https://getcomposer.org/installer | php -- --version=1.10.26 \
    && mv composer.phar /usr/local/bin/composer

# Copiar el código de la aplicación
COPY . /var/www/html

# Ajustar permisos si el directorio existe
RUN mkdir -p /var/www/html/storage /var/www/html/bootstrap/cache && \
    chown -R www-data:www-data /var/www/html && \
    chmod -R 755 /var/www/html && \
    chmod -R 775 /var/www/html/storage && \
    chmod -R 775 /var/www/html/bootstrap/cache



# Limpiar el caché de apt
# RUN apt-get clean && rm -rf /var/lib/apt/lists/*

# Instalar dependencias de Composer
# RUN composer install

# Instalar dependencias de npm
# RUN npm install

# RUN yarn install

# RUN yarn dev
# Asegurarse de que los permisos son correctos
# RUN chmod 644 /etc/phpmyadmin/config.secret.inc.php
# RUN chown www-data:www-data /etc/phpmyadmin/config.secret.inc.php

# RUN touch /usr/local/etc/php/conf.d/php_custom.ini \
#    && echo "error_reporting = E_ALL & ~E_NOTICE & ~E_STRICT & ~E_DEPRECATED" >> /usr/local/etc/php/conf.d/php_custom.ini
# FROM phusion/baseimage:jammy-1.0.0

# ENV TERM linux
# ENTRYPOINT [ "/bin/bash", "-l", "-c" ]
# CMD ["/sbin/my_init"]

# RUN apt-get update
# RUN LC_ALL=C.UTF-8 apt-get install software-properties-common -y

# # https://github.com/tianon/docker-brew-ubuntu-core/issues/48#issuecomment-215522746

# RUN LC_ALL=C.UTF-8 add-apt-repository ppa:ondrej/php -y \
#     && LC_ALL=C.UTF-8 add-apt-repository ppa:ondrej/apache2 -y \
#     && apt-get update \
#     && DEBIAN_FRONTEND=noninteractive install_clean \
#     file \
#     git \
#     imagemagick \
#     iproute2 \
#     iputils-ping \
#     libfontconfig \
#     mysql-client \
#     apache2 \
#     ntp \
#     php7.4 \
#     php7.4-cli \
#     php7.4-common \
#     php7.4-curl \
#     php7.4-fpm \
#     php7.4-gd \
#     php7.4-gmp \
#     php7.4-json \
#     php7.4-mbstring \
#     php7.4-mcrypt \
#     php7.4-mysql \
#     php7.4-opcache \
#     php7.4-sqlite3 \
#     php7.4-xml \
#     php7.4-zip \
#     python3-setuptools \
#     python3-mysqldb \
#     python3-pip \
#     wget \
#     xvfb

# RUN mkdir -p /home/amaxonia_planilla

#RUN wget -q 'https://getcomposer.org/composer.phar' --output-document=/usr/local/bin/composer \
#    && chmod a+x /usr/local/bin/composer

# RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

#EXPOSE 80

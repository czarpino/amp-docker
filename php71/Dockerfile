FROM php:7.1-apache

# Enable PDO
RUN docker-php-ext-install pdo_mysql

# Enable intl
RUN apt-get update && apt-get install -y zlib1g-dev libicu-dev g++
RUN docker-php-ext-install intl

# Install wget
RUN  apt-get update && apt-get install -y wget && rm -rf /var/lib/apt/lists/*

# Install php-soap
RUN apt-get update -y && apt-get install -y libxml2-dev php-soap && apt-get clean -y
RUN docker-php-ext-install soap

# Enable imagick
RUN apt-get update && apt-get install -y libmagickwand-dev --no-install-recommends && rm -rf /var/lib/apt/lists/*
RUN yes '' | pecl install imagick-beta

# Install mcrypt
RUN apt-get update -y && apt-get install -y libmcrypt-dev
RUN docker-php-ext-install mcrypt

# Install composer
ADD composer-install.sh /usr/local/bin/composer-install.sh
RUN /usr/local/bin/composer-install.sh && mv composer.phar /usr/bin/composer

# Install Git
RUN apt-get update && apt-get install -y git

# Install zip & unzip
RUN apt-get update && apt-get install -y zip && apt-get install -y unzip

# Setup system configurations
COPY php.ini /usr/local/etc/php/
COPY vhost.conf /etc/apache2/sites-enabled/
RUN rm /etc/apache2/sites-enabled/000-default.conf

# Enable rewrite module
RUN ln -s /etc/apache2/mods-available/rewrite.load /etc/apache2/mods-enabled/rewrite.load

# Ensure www-data has necessary permission
RUN usermod -u 1000 www-data

COPY bootstrap.sh /usr/local/bin/bootstrap.sh
CMD ["bootstrap.sh"]

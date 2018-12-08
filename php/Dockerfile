FROM php:7.2-apache
RUN apt-get update && docker-php-ext-install pdo pdo_mysql mysqli && a2enmod rewrite ssl && service apache2 restart && ln -sf /usr/share/zoneinfo/Europe/Moscow /etc/localtime

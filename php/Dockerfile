FROM php:5.6-apache 
RUN apt update && apt -y install zlib1g-dev libxml2-dev libpng-dev
RUN docker-php-ext-install mysql mysqli pdo pdo_mysql gd zip soap
COPY mysystem.conf /etc/apache2/sites-available/000-default.conf

FROM php:5.6-apache 
RUN apt-get update -qq \
	&& apt-get install -y --no-install-recommends \
         zlib1g-dev \
         libxml2-dev \
         cron \
         git \
    && docker-php-ext-install \
         mysqli \
         mysql \
         zip \
         soap \
         mbstring \
    && a2enmod rewrite

WORKDIR /var/www/html

COPY app /var/www/html

RUN curl -sS https://getcomposer.org/installer | php \
    && cd lib/pkp \
    && php ../../composer.phar update \
    && cd ../.. \
    && cd plugins/paymethod/paypal \
    && php ../../../composer.phar update \
    && cd ../../.. \
    && cd plugins/generic/citationStyleLanguage \
    && php ../../../composer.phar update \
    && cd ../../..

RUN chown -R www-data. /var/www/html

EXPOSE 80/tcp
CMD ["apache2-foreground"]

COPY mysystem.conf /etc/apache2/sites-available/000-default.conf

# Run from project root
# Docker build:
#   docker build --tag jwt-lti -f ./docker/Dockerfile .
# Start
#   docker run -it -d --name jwt-lti -v `pwd`:/var/www/html jwt-lti
# Shell
#   docker exec -it jwt-lti bash
# Tests
#   docker exec -it jwt-lti ./vendor/bin/phpunit

FROM php:7.4-fpm
COPY --from=composer:2.3.7 /usr/bin/composer /usr/local/bin/composer

RUN apt-get update
RUN apt-get install -y libmcrypt-dev wget git libpq-dev libicu-dev
#RUN pecl install mcrypt-1.0.4 && docker-php-ext-enable mcrypt
RUN docker-php-ext-configure pcntl --enable-pcntl && docker-php-ext-install pcntl

ADD . /var/www/html
WORKDIR /var/www/html

RUN composer install
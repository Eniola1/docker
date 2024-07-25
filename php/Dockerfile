FROM php:8.4.0alpha1-fpm-alpine

RUN docker-php-ext-install pdo pdo_mysql

#Run software as a super user 

ENV COMPOSER_ALLOW_SUPERUSER=1

COPY --from=composer:2.4 /usr/bin/composer /usr/bin/composer

COPY ./app/composer.* ./

#install
RUN composer install --prefer-dist --no-dev --no-scripts --no-progress --no-interaction -vvv

#use docker ps to check running containers

#copy application files to the working directory
COPY ./app .

#run composer dump-autoload --optimize
RUN composer dump-autoload --optimize   
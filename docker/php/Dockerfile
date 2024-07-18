FROM php:8.3-fpm

WORKDIR /var/www

ARG user=composer
ARG uid=1000

RUN apt-get update && apt-get install -y \
    git \
    curl \
    zip \
    unzip

# Use the default development configuration
RUN mv "$PHP_INI_DIR/php.ini-development" "$PHP_INI_DIR/php.ini"

#Copying composer from the oficial Docker composer image
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

#Creating the composer user to run the composer commands and adding the user to the www-data and root group.
RUN useradd -G www-data,root -u $uid -d /home/$user $user
#Creating the user and composer cache folders. And giving permissions
RUN mkdir -p /home/$user/.composer && \
    chown -R $user:$user /home/$user
#syntax=docker/dockerfile:1
FROM php:8.0.1-apache-buster

COPY --from=composer /usr/bin/composer /usr/bin/composer

RUN a2enmod rewrite

COPY vhost.conf /etc/apache2/sites-available
RUN a2ensite vhost.conf

WORKDIR /var/www/html

RUN docker-php-ext-install pdo pdo_mysql bcmath opcache 

# RUN docker-php-ext-install php-zip
RUN apt-get update && apt-get install -y \
    zlib1g-dev \
    libzip-dev \
    unzip \
    nodejs \
    npm

RUN docker-php-ext-install zip

ENV NODE_VERSION 12.14

RUN curl https://raw.githubusercontent.com/creationix/nvm/master/install.sh | bash

RUN . $HOME/.nvm/nvm.sh && nvm install $NODE_VERSION && nvm alias default $NODE_VERSION && nvm use default && npm install -g npm

#RUN ln -sf /root/.nvm/versions/node/v$NODE_VERSION/bin/node /usr/bin/nodejs
#RUN ln -sf /root/.nvm/versions/node/v$NODE_VERSION/bin/node /usr/bin/node
#RUN ln -sf /root/.nvm/versions/node/v$NODE_VERSION/bin/npm /usr/bin/npm

#instalando jetstream
RUN composer require laravel/jetstream
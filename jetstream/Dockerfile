#syntax=docker/dockerfile:1
FROM bitnami/laravel:8

#COPY --from=composer /usr/bin/composer /usr/bin/composer

#instalando jetstream
RUN composer require laravel/jetstream
#RUN php artisan jetstream:install inertia
#RUN php artisan jetstream:install inertia --teams
#RUN php artisan migrate
#RUN php artisan key:generate

RUN npm install && run dev
    
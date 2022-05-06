FROM php:8.1-fpm
WORKDIR "/application"

RUN apt-get update
RUN apt-get install libyaml-dev zlib1g-dev libpng-dev libwebp-dev libjpeg-dev libfreetype6-dev librabbitmq-dev libxml2-dev libzip-dev libpq-dev git zip libonig-dev -y
RUN pecl install yaml
RUN pecl install redis
RUN pecl install mongodb
RUN pecl install amqp
RUN docker-php-ext-enable yaml
RUN docker-php-ext-enable redis
RUN docker-php-ext-enable mongodb
RUN docker-php-ext-enable amqp
RUN PHP_OPENSSL=yes
RUN docker-php-ext-configure gd --with-freetype --with-jpeg --with-webp
RUN docker-php-ext-install \
    xml \
    pgsql \
    filter \
    bcmath \
    zip \
    gd \
    intl \
    mbstring

RUN apt-get clean; rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*

COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

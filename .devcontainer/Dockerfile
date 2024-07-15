
FROM php:8.2-fpm

RUN apt-get update && apt-get install -y \
    zlib1g-dev \
    libzip-dev \
    unzip
RUN docker-php-ext-install zip

COPY --from=composer /usr/bin/composer /usr/bin/composer
RUN composer self-update

RUN curl -sS https://get.symfony.com/cli/installer | bash
RUN mv /root/.symfony5/bin/symfony /usr/local/bin/symfony

RUN apt -y update
RUN apt -y install git

RUN pecl install xdebug-3.2.1 \
	&& docker-php-ext-enable xdebug

FROM php:7.4-fpm-alpine
WORKDIR /var/www/app

RUN apk update && apk upgrade && apk add --no-cache \
	bash \
    mc \
    git \
    supervisor \
    tzdata

RUN apk add --no-cache $PHPIZE_DEPS \
    && pecl install xdebug-2.9.2 \
    && docker-php-ext-enable xdebug

ENV TZ=Europe/Moscow
RUN cp /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
RUN addgroup -g 1000 dev && adduser -u 1000 -G dev -s /bin/bash -D dev
COPY --chown=dev:dev / /var/www/app
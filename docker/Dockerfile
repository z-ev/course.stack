FROM php:7.4-fpm-alpine
WORKDIR /var/www/stack

RUN apk update && apk upgrade && apk add --no-cache \
	bash \
    openssh \
    git \
    libjpeg-turbo-dev \
    oniguruma-dev \
    freetype-dev \
    libxml2-dev \
    libzip-dev \
    libpng-dev \
    supervisor \
    curl-dev \
    gettext \
    curl \
	libmcrypt-dev \
	icu-dev \
    libxslt-dev \
    php7-mcrypt \
    tzdata

RUN docker-php-ext-install -j$(nproc) \
    pdo_mysql \
    tokenizer \
    mbstring \
	ctype \
    iconv \
	json \
    curl \
	pdo \
	xml \
	zip \
	&& docker-php-ext-configure gd --with-freetype --with-jpeg \
	&& docker-php-ext-install -j$(nproc) gd \
	&& curl -sS https://getcomposer.org/installer -o composer-setup.php \
	&& php composer-setup.php --install-dir=/usr/local/bin --filename=composer


RUN docker-php-ext-configure intl
RUN docker-php-ext-install intl \
    xsl \
    soap \
    sockets \
    bcmath

RUN apk add --no-cache $PHPIZE_DEPS \
    && pecl install xdebug-2.9.2 \
    && docker-php-ext-enable xdebug

ENV TZ=Europe/Moscow
RUN cp /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
RUN addgroup -g 1000 dev && adduser -u 1000 -G dev -s /bin/bash -D dev
COPY --chown=dev:dev / /var/www/app
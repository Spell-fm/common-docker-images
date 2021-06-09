FROM php:7.4-alpine

RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.aliyun.com/g' /etc/apk/repositories

COPY --from=composer /usr/bin/composer /usr/bin/composer

RUN apk add --no-cache --virtual .build-deps \
    $PHPIZE_DEPS \
    imagemagick-dev

RUN apk add --no-cache \
    freetype-dev \
    icu-dev \
    icu-libs \
    imagemagick \
    libjpeg-turbo-dev \
    libpng-dev \
    libzip-dev

RUN docker-php-ext-install \
    bcmath \
    calendar \
    gd \
    intl \
    pdo_mysql \
    zip

RUN pecl install \
    imagick \
    pcov

RUN docker-php-ext-enable \
    imagick \
    pcov

RUN docker-php-ext-configure gd --with-freetype --with-jpeg

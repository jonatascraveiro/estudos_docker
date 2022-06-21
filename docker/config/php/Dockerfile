FROM php:7.4-fpm-alpine

RUN apk update --no-cache \
&& apk add \
icu-dev \
oniguruma-dev \
tzdata



RUN apk add --update --no-cache openssl bash postgresql-dev gnupg unzip zip php-pgsql ldb-dev zlib-dev \
    freetype-dev \
    libpng-dev \
    jpeg-dev \
    libjpeg-turbo-dev \
    libxml2-dev \
    libzip \
    libzip-dev

RUN docker-php-ext-configure zip
RUN docker-php-ext-install zip

#RUN apk add --no-cache libzip-dev && docker-php-ext-configure zip --with-libzip=/usr/include && docker-php-ext-install zip
#RUN docker-php-ext-configure zip
#RUN docker-php-ext-configure zip
#RUN docker-php-ext-configure zip --with-zlib-dir=/usr/include

#zlib

RUN docker-php-ext-install pdo pgsql pdo_pgsql

#libs necessarias para o laravelexcel
RUN docker-php-ext-install gd xml simplexml

RUN docker-php-ext-install intl

RUN docker-php-ext-install pcntl

#RUN docker-php-ext-install pdo_mysql

RUN docker-php-ext-install mbstring

#RUN docker-php-ext-install gd
#RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ --with-png-dir=/usr/include/ && \

RUN rm -rf /var/cache/apk/*

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/bin --filename=composer

CMD ["php-fpm"]

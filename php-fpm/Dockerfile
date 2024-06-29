FROM php:7.2-fpm

# always run apt update when start and after add new source list, then clean up at end.
RUN apt-get update -yqq && \
    pecl channel-update pecl.php.net && \
    apt-get install -yqq apt-utils

RUN apt-get update \
  && apt-get install -y \
    curl \
    libz-dev \
    libpq-dev \
    libjpeg-dev \
    libpng-dev \
    libfreetype6-dev \
    libssl-dev \
    libbz2-dev \
    libjpeg62-turbo-dev

USER root

RUN docker-php-ext-configure mbstring --enable-mbstring && \
    docker-php-ext-install mbstring

RUN docker-php-ext-configure pdo_mysql --with-pdo-mysql && \
    docker-php-ext-install pdo_mysql

RUN apt-get install -y zlib1g-dev libicu-dev g++ && \
    docker-php-ext-configure intl && \
    docker-php-ext-install intl

RUN docker-php-ext-configure bcmath --enable-bcmath && \
    docker-php-ext-install bcmath

RUN docker-php-ext-configure pcntl --enable-pcntl && \
    docker-php-ext-install pcntl

RUN pecl install -o -f redis && \
    docker-php-ext-enable redis

RUN apt-get install -y libzip-dev && \
    docker-php-ext-configure zip --with-libzip && \
    docker-php-ext-install zip && \
    php -m | grep -q 'zip'

RUN docker-php-ext-install sockets

RUN docker-php-ext-install opcache && \
    docker-php-ext-enable opcache

RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install gd

RUN rm /etc/apt/preferences.d/no-debian-php && \
    apt-get install -y libxml2-dev php-soap && \
    docker-php-ext-configure soap --enable-soap && \
    docker-php-ext-install soap

RUN apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* && \
    rm /var/log/lastlog /var/log/faillog

CMD ["php-fpm"]

EXPOSE 9000

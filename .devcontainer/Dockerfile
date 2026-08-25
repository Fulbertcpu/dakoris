FROM php:8.3-apache

RUN apt-get update && apt-get install -y \
    libicu-dev \
    libxml2-dev \
    libzip-dev \
    libpng-dev \
    libjpeg62-turbo-dev \
    libfreetype6-dev \
    libonig-dev \
    gettext \
    unzip \
    git \
    git-lfs \
    curl \
    && docker-php-ext-configure gd \
        --with-freetype \
        --with-jpeg \
    && docker-php-ext-install \
        mysqli \
        pdo_mysql \
        mbstring \
        curl \
        zip \
        xml \
        gd \
        intl \
        gettext \
    && a2enmod rewrite \
    && git lfs install \
    && rm -rf /var/lib/apt/lists/*

COPY --from=composer:2 /usr/bin/composer /usr/bin/composer

WORKDIR /var/www/html

FROM php:7.4-fpm

RUN apt-get update && apt-get install -y \
    libpng-dev \
    libjpeg-dev \
    libfreetype6-dev \
    zip \
    unzip \
    git \
    curl

RUN docker-php-ext-configure gd --with-freetype --with-jpeg
RUN docker-php-ext-install gd pdo pdo_mysql
RUN apt-get clean && rm -rf /var/lib/apt/lists/*
WORKDIR /var/www/html
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer
EXPOSE 9000
CMD ["php-fpm"]

FROM php:8.2-fpm

# Install dependencies
RUN apt-get update && apt-get install -y \
    build-essential \
    libpng-dev \
    libjpeg62-turbo-dev \
    libfreetype6-dev \
    locales \
    zip \
    jpegoptim optipng pngquant gifsicle \
    vim \
    unzip \
    git \
    curl \
    libzip-dev \
    zlib1g-dev \
    libicu-dev \
    libpq-dev \
    g++ \
    sudo \
    libz-dev \
    libmemcached-dev \
    sendmail 

# Install nodejs
RUN curl -sL https://deb.nodesource.com/setup_18.x | sudo -E bash -
RUN apt-get install -y nodejs

# Clear cache
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

# Install extensions
RUN docker-php-ext-install pdo pdo_pgsql
RUN docker-php-ext-configure gd --with-jpeg --with-freetype
RUN docker-php-ext-configure intl
RUN docker-php-ext-install gd intl
RUN docker-php-ext-install opcache

# Install composer
RUN curl -sS https://getcomposer.org/installer | php -- \ 
    --install-dir=/usr/local/bin --filename=composer && chmod +x /usr/local/bin/composer

# Install xdebug by pecl
RUN pecl install xdebug && docker-php-ext-enable xdebug

# Add user www
RUN groupadd -g 1000 www
RUN useradd -u 1000 -ms /bin/bash -g www www

# Change current user to www
USER www

# Set working directory
WORKDIR /var/www

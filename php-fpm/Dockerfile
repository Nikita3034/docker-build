FROM php:7.4-fpm

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
    g++ \
    sudo \
    libz-dev \
    libmemcached-dev \
    sendmail 

# Clear cache
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

# Install extensions
RUN docker-php-ext-install pdo_mysql zip exif pcntl bcmath mysqli
RUN docker-php-ext-configure gd --with-jpeg --with-freetype
RUN docker-php-ext-configure intl
RUN docker-php-ext-install gd intl
RUN docker-php-ext-install opcache

# Install composer
RUN curl -sS https://getcomposer.org/installer | php -- \ 
    --install-dir=/usr/local/bin --filename=composer && chmod +x /usr/local/bin/composer

# Install xdebug
RUN pecl install xdebug-2.9.1 \
    && docker-php-ext-enable xdebug
COPY xdebug.ini $PHP_INI_DIR/conf.d/xdebug.ini

# Install node and npm
RUN curl -sL https://deb.nodesource.com/setup_16.x -o setup_16.sh
RUN sh ./setup_16.sh
RUN apt update
RUN apt install nodejs
RUN npm i -g npm@7.24.2

# Add user www
RUN groupadd -g 1000 www
RUN useradd -u 1000 -ms /bin/bash -g www www

# Change current user to www
USER www

# Set working directory
WORKDIR /var/www

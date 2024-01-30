FROM php:8.3.1-fpm

# Current user to root
USER root

# Set working directory
WORKDIR /var/www

# Install dependencies
RUN apt-get update && apt-get install -y \
    build-essential \
    libzip-dev \
    libc6 \
    libxpm-dev \
    zlib1g \
    locales \
    zip \
    vim \
    unzip \
    git \
    curl \
    libpq-dev \
    libonig-dev

# Clear cache
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

# Install extensions
RUN docker-php-ext-install pdo_mysql zip

# Install composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Cleaning
RUN apt-get clean && apt-get autoremove -y
RUN rm -rf /var/lib/apt/lists/*

# Current user to www-data
USER www-data

# Expose port 9000 and start php-fpm server
EXPOSE 9000
CMD ["php-fpm"]

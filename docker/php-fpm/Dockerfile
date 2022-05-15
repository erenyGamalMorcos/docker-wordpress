FROM php:8.0-fpm

# install needed apps
RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y vim && \
# PHP Core Extensions (GD & SSL)
	apt-get install -y --no-install-recommends \
        libfreetype6-dev \
		libjpeg-dev \
		libmagickwand-dev \
		libpng-dev \
		libzip-dev \
		libcurl4-openssl-dev pkg-config libssl-dev \
        ghostscript \
# https://make.wordpress.org/hosting/handbook/handbook/server-environment/#php-extensions
	&& docker-php-ext-install -j "$(nproc)" \
		bcmath \
		sockets \
		exif \
		gd \
		mysqli \
		opcache \
		zip \
		soap	


# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Install WP-CLI
RUN curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar && \
    chmod +x wp-cli.phar && \
    mv wp-cli.phar /usr/local/bin/wp


WORKDIR /var/www/html
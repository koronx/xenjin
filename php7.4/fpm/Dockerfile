FROM php:7.4-fpm-alpine
RUN apk add git wget zlib \
    && rm -rf /var/cache/apk/*

#        && docker-php-ext-enable gd mysqli \

COPY --from=mlocati/php-extension-installer /usr/bin/install-php-extensions /usr/local/bin/

RUN install-php-extensions mysqli gd zip redis

#RUN docker-php-ext-install mysqli gd pdo curl zip xml mbstring

COPY conf/php.ini /usr/local/etc/php/conf.d/50-setting.ini
COPY conf/www.conf /usr/local/etc/php-fpm.d/www.conf

# Install composer from the official image
COPY --from=composer /usr/bin/composer /usr/bin/composer

# Run composer install to install the dependencies
#RUN composer install --optimize-autoloader --no-interaction --no-progress

#EXPOSE 9000
#CMD ["php-fpm5", "-F"]
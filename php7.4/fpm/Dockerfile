FROM php:7.4-fpm-alpine
RUN apk add git wget zip \
        && docker-php-ext-enable zip curl redis mysql \
    && rm -rf /var/cache/apk/*

#COPY conf/php.ini /etc/php5/conf.d/50-setting.ini
#COPY conf/php-fpm.conf /etc/php5/php-fpm.conf
#RUN ln -s /usr/bin/php5 /usr/bin/php

# Install composer from the official image
COPY --from=composer /usr/bin/composer /usr/bin/composer

# Run composer install to install the dependencies
#RUN composer install --optimize-autoloader --no-interaction --no-progress

#EXPOSE 9000
#CMD ["php-fpm5", "-F"]
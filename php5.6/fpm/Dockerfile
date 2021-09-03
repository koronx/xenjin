FROM alpine:3.8
RUN apk add \
        php5 \
        php5-cli \
        php5-bcmath \
        php5-dom \
        php5-ctype \
        php5-curl \
        php5-fpm \
        php5-gd \
        php5-iconv \
        php5-intl \
        php5-json \
        php5-mcrypt \
        php5-opcache \
        php5-openssl \
        php5-pdo \
        php5-pdo_mysql \
        php5-pdo_sqlite \
        php5-phar \
        php5-posix \
        php5-soap \
        php5-xml \
        php5-zip \
        php5-zlib \
        git \
        wget \
    && rm -rf /var/cache/apk/*
RUN apk --no-cache add ca-certificates wget && wget --quiet --output-document=/etc/apk/keys/sgerrand.rsa.pub https://alpine-pkgs.sgerrand.com/sgerrand.rsa.pub && wget https://github.com/sgerrand/alpine-pkg-php5-redis/releases/download/3.1.6-r0/php5-redis-3.1.6-r0.apk && apk add php5-redis-3.1.6-r0.apk
COPY conf/php.ini /etc/php5/conf.d/50-setting.ini
COPY conf/php-fpm.conf /etc/php5/php-fpm.conf
RUN ln -s /usr/bin/php5 /usr/bin/php

# Install composer from the official image
COPY --from=composer /usr/bin/composer /usr/bin/composer

# Run composer install to install the dependencies
#RUN composer install --optimize-autoloader --no-interaction --no-progress

EXPOSE 9000
CMD ["php-fpm5", "-F"]
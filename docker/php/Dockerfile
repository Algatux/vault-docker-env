FROM php:8-fpm

RUN docker-php-ext-install pdo_mysql intl \
    && docker-php-source delete

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN useradd -m -G sudo,www-data php-user \
    && chown -R php-user:php-user /home/php-user

USER php-user

COPY etc/conf.d/ /usr/local/etc/php/conf.d/
COPY etc/conf.d/php-fpm.conf /usr/local/etc/php-fpm.d/dv-project.conf

WORKDIR /home/php-user/project

EXPOSE 9000

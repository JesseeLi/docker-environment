FROM php:8.2.17-fpm

RUN apt-get update && apt-get upgrade -y \
    && apt-get install -y git vim zlib1g-dev unzip zip libzip-dev\
    && rm -rf /var/lib/apt/lists/* \
    && pecl install redis-6.0.2\
    && docker-php-ext-enable redis\
    && docker-php-ext-install -j$(nproc) bcmath pdo_mysql zip

RUN groupmod -o -g 1000 www-data \
    && usermod -o -u 1000 -g www-data www-data

RUN cd /tmp \
    && php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
    && php -r "if (hash_file('sha384', 'composer-setup.php') === 'dac665fdc30fdd8ec78b38b9800061b4150413ff2e3b6f88543c636f7cd84f6db9189d43a81e5503cda447da73c7e5b6') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"\
    && php composer-setup.php \ 
    && php -r "unlink('composer-setup.php');" \
    && mv composer.phar /usr/local/bin/composer \
    && composer config -g repo.packagist composer https://mirrors.aliyun.com/composer/

WORKDIR /var/www

CMD [ "php-fpm" ]

EXPOSE 9000
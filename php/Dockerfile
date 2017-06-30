FROM php:7-fpm

RUN apt update && \
    apt full-upgrade -y && \
    apt install -y curl wget git nano libfreetype6-dev libjpeg62-turbo-dev libmcrypt-dev libpng12-dev libicu-dev libicu52

RUN curl -sLS https://deb.nodesource.com/setup_8.x | bash - && \
    curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add - && \
    echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list && \
    apt update && \
    apt install -y nodejs yarn

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN docker-php-ext-install iconv && \
    docker-php-ext-install exif && \
    docker-php-ext-install mbstring && \
    docker-php-ext-install pdo_mysql && \
    docker-php-ext-install pdo && \
    docker-php-ext-install intl && \
    docker-php-ext-install opcache && \
    docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ && \
    docker-php-ext-install gd && \
    docker-php-ext-install zip

COPY php.ini /usr/local/etc/php/conf.d/
COPY default.conf /usr/local/etc/php-fpm.d/www.conf
COPY initialise-sylius /usr/local/bin/initialise-sylius
RUN chmod +x /usr/local/bin/initialise-sylius
EXPOSE 9000

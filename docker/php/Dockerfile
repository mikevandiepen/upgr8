ARG version

# Loading the container with the version as declared in .env[DOCKER_PHP_VERSION].
FROM php:${version}-fpm

# Adding xDebug to the PHP Runtime.
RUN pecl install -o -f xdebug \
    && docker-php-ext-enable xdebug

# Adding the xdebug socket to the xdebug.ini file.
RUN echo "zend_extension=$(find $(php-config --extension-dir) -name xdebug.so)" > /usr/local/etc/php/conf.d/xdebug.ini

# Enabling Mysql
RUN docker-php-ext-configure pdo_mysql --with-pdo-mysql=mysqlnd \
    && docker-php-ext-configure mysqli --with-mysqli=mysqlnd \
    && docker-php-ext-install pdo_mysql

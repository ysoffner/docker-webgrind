FROM php:5.6.30-fpm

LABEL Maintainer="Yuri Soffner <ysoffner@gmail.com>" \
      Description="Lightweight php 5.6.30 container based on php.image with xDebug enabled & composer installed." \
      Description="11 line - Need to generate Webgrind Call Graph" \
      org.label-schema.name="php-5.6.30-xdebug-php.image" \
      org.label-schema.schema-version="1.0.0"

RUN apt-get update && \
  apt-get install -y zlib1g-dev php5-mysql libfreetype6-dev libjpeg62-turbo-dev \
  libmcrypt-dev libpng12-dev python-dev graphviz libgraphviz-dev pkg-config python-pip \
    && pip install pygraphviz \
    && docker-php-ext-install -j$(nproc) iconv mcrypt \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ --with-png-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd \
    && docker-php-ext-install mysqli mysql pdo_mysql zip

RUN pecl install xdebug-2.5.5 \
  && docker-php-ext-enable xdebug \
  && echo "zend_extension=/usr/local/lib/php/extensions/no-debug-non-zts-20131226/xdebug.so" > /usr/local/etc/php/conf.d/ext-xdebug.ini \
  && echo "xdebug.profiler_enable = 1" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
  && echo "xdebug.profiler_output_name = xdebug.out.%t" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
  && echo "xdebug.profiler_output_dir = /tmp" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
  && echo "xdebug.profiler_enable_trigger = 1" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini

RUN pecl install redis-3.1.4 \
  && docker-php-ext-enable redis

WORKDIR /var/www
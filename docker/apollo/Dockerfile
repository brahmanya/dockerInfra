FROM ubuntu:16.04
ENV LANG C.UTF-8
ENV DEBIAN_FRONTEND noninteractive

RUN ln -sf /usr/share/zoneinfo/Asia/Bangkok /etc/localtime

RUN apt-get update && apt-get -y upgrade && \
    apt-get -y install -q supervisor \
                       cron \
                       nginx \
                       unzip \
                       git \
                       curl \
                       libxrender1 \
                       libthai0 \
                       xfonts-thai \
                       php7.0-fpm \
                       php7.0-cli \
                       php7.0-gd \
                       php7.0-imap \
                       php7.0-intl \
                       php7.0-json \
                       php7.0-mcrypt \
                       php7.0-mysql \
                       php7.0-mbstring \
                       php7.0-ldap \
                       php7.0-zip \
                       php7.0-xml \
                       php7.0-curl \
                       php7.0-soap && \
                       apt-get clean

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer && chmod +x /usr/local/bin/composer

WORKDIR /var/www

ADD conf/php.ini /etc/php/7.0/fpm/conf.d/99-custom.ini
ADD conf/www.conf /etc/php/7.0/fpm/pool.d/www.conf
ADD conf/nginx.conf /etc/nginx/nginx.conf
ADD conf/env.devel /var/www/.env

RUN mkdir /var/run/php/
RUN useradd -u 1000 1000


FROM alpine:3.16

LABEL maintainer="joblocal GmbH <produktentwicklung@joblocal.de>"

ENV PHP_OPCACHE_VALIDATE_TIMESTAMPS="0" \
    PHP_OPCACHE_MAX_ACCELERATED_FILES="30000" \
    PHP_OPCACHE_MEMORY_CONSUMPTION="192" \
    PHP_OPCACHE_MAX_WASTED_PERCENTAGE="10"

RUN adduser -u 1000 -D -S -G www-data www-data

RUN apk add --no-cache --update \
  bash \
  ca-certificates \
  memcached \
  nginx \
  nginx-mod-http-headers-more \
  php81 \
  php81-ctype \
  php81-curl \
  php81-dom \
  php81-fpm \
  php81-json \
  php81-mbstring \
  php81-pecl-memcached \
  php81-pdo_mysql \
  php81-pdo_sqlite \
  php81-simplexml \
  php81-xml \
  php81-opcache \
  php81-tokenizer \
  php81-pecl-apcu \
  php81-bcmath \
  php81-fileinfo \
  php81-xmlwriter \
  runit \
  && ln -sf /dev/stdout /var/log/nginx/access.log \
  && ln -sf /dev/stderr /var/log/nginx/error.log \
  && ln -s /usr/bin/php81 /usr/bin/php

# Set Timezone to UTC
RUN apk add --no-cache --update tzdata \
  && cp /usr/share/zoneinfo/UTC /etc/localtime \
  && echo "UTC" >  /etc/timezone \
  && apk del tzdata

COPY ./rootfs /

RUN chmod +x /sbin/runit-wrapper \
             /sbin/runsvdir-start \
             /etc/service/nginx/run \
             /etc/service/php-fpm/run

EXPOSE 80

CMD ["/sbin/runit-wrapper"]

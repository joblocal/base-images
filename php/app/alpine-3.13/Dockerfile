FROM alpine:3.13

LABEL maintainer="joblocal GmbH <produktentwicklung@joblocal.de>"

ENV PHP_OPCACHE_VALIDATE_TIMESTAMPS="0" \
    PHP_OPCACHE_MAX_ACCELERATED_FILES="30000" \
    PHP_OPCACHE_MEMORY_CONSUMPTION="192" \
    PHP_OPCACHE_MAX_WASTED_PERCENTAGE="10"

RUN addgroup -g 1000 -S www-data \
  && adduser -u 1000 -D -S -G www-data www-data

RUN apk add --no-cache --update \
  bash \
  ca-certificates \
  memcached \
  nginx \
  nginx-mod-http-headers-more \
  php8 \
  php8-ctype \
  php8-curl \
  php8-dom \
  php8-fpm \
  php8-json \
  php8-mbstring \
  php8-pecl-memcached \
  php8-pdo_mysql \
  php8-pdo_sqlite \
  php8-simplexml \
  php8-xml \
  php8-opcache \
  php8-tokenizer \
  php8-pecl-apcu \
  php8-bcmath \
  php8-fileinfo \
  runit \
  && ln -sf /dev/stdout /var/log/nginx/access.log \
  && ln -sf /dev/stderr /var/log/nginx/error.log \
  && ln -s /usr/bin/php8 /usr/bin/php

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

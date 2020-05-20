FROM alpine:3.11

LABEL maintainer="joblocal GmbH <produktentwicklung@joblocal.de>"

RUN addgroup -g 1000 -S www-data \
  && adduser -u 1000 -D -S -G www-data www-data

RUN apk add --no-cache --update \
  bash \
  ca-certificates \
  memcached \
  nginx \
  nginx-mod-http-headers-more \
  php7 \
  php7-ctype \
  php7-curl \
  php7-dom \
  php7-fpm \
  php7-json \
  php7-mbstring \
  php7-memcached \
  php7-pdo_mysql \
  php7-pdo_sqlite \
  php7-simplexml \
  php7-xml \
  php7-opcache \
  runit \
  && ln -sf /dev/stdout /var/log/nginx/access.log \
  && ln -sf /dev/stderr /var/log/nginx/error.log


# Set Timezone to UTC
RUN apk add --no-cache --update tzdata \
  && cp /usr/share/zoneinfo/UTC /etc/localtime \
  && echo "UTC" >  /etc/timezone \
  && apk del tzdata

COPY ./rootfs /

EXPOSE 80

CMD ["/sbin/runit-wrapper"]

FROM alpine:3.8

LABEL maintainer="joblocal GmbH <produktentwicklung@joblocal.de>"

RUN addgroup -g 1000 -S www-data \
  && adduser -u 1000 -D -S -G www-data www-data

RUN apk add --update \
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
  runit \
  && rm -rf /var/cache/apk/* \
  && ln -sf /dev/stdout /var/log/nginx/access.log \
  && ln -sf /dev/stderr /var/log/nginx/error.log


# Set Timezone to UTC and remove apk cache
RUN apk add --update tzdata \
  && cp /usr/share/zoneinfo/UTC /etc/localtime \
  && echo "UTC" >  /etc/timezone \
  && apk del tzdata \
  && rm -rf /var/cache/apk/*

COPY ./rootfs /

EXPOSE 80

CMD ["/sbin/runit-wrapper"]

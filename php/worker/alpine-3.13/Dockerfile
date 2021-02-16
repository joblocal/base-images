FROM alpine:3.13

LABEL maintainer="joblocal GmbH <produktentwicklung@joblocal.de>"

RUN addgroup -g 1000 -S www-data \
  && adduser -u 1000 -D -S -G www-data www-data

RUN apk add --no-cache --update \
  bash \
  ca-certificates \
  memcached \
  php8 \
  php8-ctype \
  php8-curl \
  php8-dom \
  php8-json \
  php8-mbstring \
  php8-pecl-memcached \
  php8-pdo_mysql \
  php8-pdo_sqlite \
  php8-simplexml \
  php8-xml \
  php8-tokenizer \
  php8-pecl-apcu \
  php8-bcmath \
  php8-fileinfo \
  runit \
  && ln -s /usr/bin/php8 /usr/local/bin/php

# Set Timezone to UTC
RUN apk add --no-cache --update tzdata \
  && cp /usr/share/zoneinfo/UTC /etc/localtime \
  && echo "UTC" >  /etc/timezone \
  && apk del tzdata

COPY ./rootfs /

CMD ["/usr/bin/queuelistener.sh"]

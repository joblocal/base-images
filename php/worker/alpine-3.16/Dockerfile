FROM alpine:3.16

LABEL maintainer="joblocal GmbH <produktentwicklung@joblocal.de>"

RUN adduser -u 1000 -D -S -G www-data www-data

RUN apk add --no-cache --update \
  bash \
  ca-certificates \
  memcached \
  php81 \
  php81-ctype \
  php81-curl \
  php81-dom \
  php81-json \
  php81-mbstring \
  php81-pecl-memcached \
  php81-pdo_mysql \
  php81-pdo_sqlite \
  php81-simplexml \
  php81-xml \
  php81-tokenizer \
  php81-pecl-apcu \
  php81-bcmath \
  php81-fileinfo \
  php81-xmlwriter \
  runit \
  && ln -s /usr/bin/php81 /usr/bin/php

# Set Timezone to UTC
RUN apk add --no-cache --update tzdata \
  && cp /usr/share/zoneinfo/UTC /etc/localtime \
  && echo "UTC" >  /etc/timezone \
  && apk del tzdata

COPY ./rootfs /

CMD ["/usr/bin/queuelistener.sh"]

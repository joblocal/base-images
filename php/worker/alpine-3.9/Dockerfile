FROM alpine:3.9

LABEL maintainer="joblocal GmbH <produktentwicklung@joblocal.de>"

RUN addgroup -g 1000 -S www-data \
  && adduser -u 1000 -D -S -G www-data www-data

RUN apk add --no-cache --update \
  bash \
  ca-certificates \
  memcached \
  php7 \
  php7-ctype \
  php7-curl \
  php7-dom \
  php7-json \
  php7-mbstring \
  php7-memcached \
  php7-pdo_mysql \
  php7-pdo_sqlite \
  php7-simplexml \
  php7-xml \
  runit

# Set Timezone to UTC
RUN apk add --no-cache --update tzdata \
  && cp /usr/share/zoneinfo/UTC /etc/localtime \
  && echo "UTC" >  /etc/timezone \
  && apk del tzdata

COPY ./rootfs /

CMD ["/usr/bin/queuelistener.sh"]

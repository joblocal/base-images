FROM joblocal/base-app:alpine-3.16

LABEL maintainer="joblocal GmbH <produktentwicklung@joblocal.de>"

RUN apk add --no-cache --update \
  composer \
  curl \
  ghostscript \
  git \
  imagemagick \
  jq \
  nodejs \
  php81-pecl-apcu \
  php81-fileinfo \
  php81-iconv \
  php81-pecl-imagick \
  php81-opcache \
  php81-phar \
  php81-tokenizer \
  php81-xmlwriter \
  php81-xsl \
  php81-tokenizer \
  php81-pecl-apcu \
  php81-bcmath \
  php81-fileinfo \
  python3 \
  rsync \
  unzip \
  yarn \
  zip \
  rust \
  cargo \
  docker-compose \
  && if [ ! -e /usr/bin/python ]; then ln -sf python3 /usr/bin/python ; fi \
  && rm -f /usr/bin/php && ln -s /usr/bin/php81 /usr/bin/php

RUN curl "https://s3.amazonaws.com/aws-cli/awscli-bundle.zip" -o "awscli-bundle.zip" \
  && unzip awscli-bundle.zip \
  && ./awscli-bundle/install -b /usr/local/bin/aws \
  && rm -f awscli-bundle.zip

RUN yarn global add @joblocal/aws-cfn-deployment

WORKDIR /workspace

VOLUME /workspace

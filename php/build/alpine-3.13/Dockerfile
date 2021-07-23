FROM joblocal/base-app:alpine-3.13

LABEL maintainer="joblocal GmbH <produktentwicklung@joblocal.de>"

RUN apk add --no-cache --update \
  composer \
  curl \
  ghostscript \
  git \
  imagemagick \
  jq \
  nodejs \
  php8-pecl-apcu \
  php8-fileinfo \
  php8-iconv \
  php8-pecl-imagick \
  php8-opcache \
  php8-phar \
  php8-tokenizer \
  php8-xmlwriter \
  php8-xsl \
  php8-tokenizer \
  php8-pecl-apcu \
  php8-bcmath \
  php8-fileinfo \
  python3 \
  rsync \
  unzip \
  yarn \
  zip \
  rust \
  cargo \
  && if [ ! -e /usr/bin/python ]; then ln -sf python3 /usr/bin/python ; fi \
  && rm -f /usr/bin/php && ln -s /usr/bin/php8 /usr/bin/php

RUN curl "https://s3.amazonaws.com/aws-cli/awscli-bundle.zip" -o "awscli-bundle.zip" \
  && unzip awscli-bundle.zip \
  && ./awscli-bundle/install -b /usr/local/bin/aws \
  && rm -f awscli-bundle.zip

RUN apk add --no-cache --update --virtual pip3-install-docker-compose \
  gcc \
  libc-dev \
  libffi-dev \
  make \
  openssl-dev \
  py3-pip \
  python3-dev \
  && pip3 install --no-cache-dir docker-compose \
  && apk del pip3-install-docker-compose

RUN yarn global add @joblocal/aws-cfn-deployment

WORKDIR /workspace

VOLUME /workspace

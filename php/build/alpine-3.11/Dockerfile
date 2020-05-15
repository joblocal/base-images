FROM joblocal/base-app:alpine-3.11

LABEL maintainer="joblocal GmbH <produktentwicklung@joblocal.de>"

RUN apk add --no-cache --update \
  composer \
  curl \
  ghostscript \
  git \
  imagemagick \
  jq \
  nodejs \
  php7-apcu \
  php7-fileinfo \
  php7-iconv \
  php7-imagick \
  php7-opcache \
  php7-phar \
  php7-tokenizer \
  php7-xmlwriter \
  php7-xsl \
  python2 \
  rsync \
  unzip \
  yarn \
  zip

RUN curl "https://s3.amazonaws.com/aws-cli/awscli-bundle.zip" -o "awscli-bundle.zip" \
  && unzip awscli-bundle.zip \
  && ./awscli-bundle/install -b /usr/local/bin/aws \
  && rm -f awscli-bundle.zip

RUN apk add --no-cache --update --virtual pip-install-docker-compose \
  gcc \
  libc-dev \
  libffi-dev \
  make \
  openssl-dev \
  py-pip \
  python-dev \
  && pip install --no-cache-dir docker-compose \
  && apk del pip-install-docker-compose

RUN yarn global add @joblocal/aws-cfn-deployment

WORKDIR /workspace

VOLUME /workspace

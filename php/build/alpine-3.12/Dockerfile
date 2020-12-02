FROM joblocal/base-app:alpine-3.12

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
  php7-tokenizer \
  php7-apcu \
  php7-bcmath \
  php7-fileinfo \
  python3 \
  rsync \
  unzip \
  yarn \
  zip \
  && if [ ! -e /usr/bin/python ]; then ln -sf python3 /usr/bin/python ; fi

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

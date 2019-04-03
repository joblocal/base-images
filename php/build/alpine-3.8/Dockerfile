FROM joblocal/base-app:alpine-3.8

LABEL maintainer="joblocal GmbH <produktentwicklung@joblocal.de>"

RUN apk add --update \
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
  php7-simplexml \
  php7-tokenizer \
  php7-xsl \
  py-pip \
  python2 \
  rsync \
  unzip \
  yarn \
  zip \
  && rm -rf /var/cache/apk/*

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer \
  && curl "https://s3.amazonaws.com/aws-cli/awscli-bundle.zip" -o "awscli-bundle.zip" \
  && unzip awscli-bundle.zip \
  && ./awscli-bundle/install -b /usr/local/bin/aws \
  && rm -f awscli-bundle.zip

RUN pip install --no-cache-dir docker-compose~=1.23.0

RUN yarn global add @joblocal/aws-cfn-deployment

WORKDIR /workspace

VOLUME /workspace

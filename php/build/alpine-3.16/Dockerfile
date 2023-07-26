FROM joblocal/base-app:alpine-3.16

LABEL maintainer="joblocal GmbH <produktentwicklung@joblocal.de>"

RUN apk add --no-cache --update \
  curl \
  curl-dev \
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

# Installing composer with apk adds as a dependency a php version that
# is older than 8.1 and because of this composer install fails on the container
# so we opt for a manual install here as per https://getcomposer.org/download/
# Latest: v2.5.8
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" && \
    php -r "if (hash_file('sha384', 'composer-setup.php') === 'e21205b207c3ff031906575712edab6f13eb0b361f2085f1f1237b7126d785e826a450292b6cfd1d64d92e6563bbde02') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;" && \
     php composer-setup.php && \
     php -r "unlink('composer-setup.php');" && \
     mv composer.phar /usr/local/bin/composer;

RUN curl "https://s3.amazonaws.com/aws-cli/awscli-bundle.zip" -o "awscli-bundle.zip" \
  && unzip awscli-bundle.zip \
  && ./awscli-bundle/install -b /usr/local/bin/aws \
  && rm -f awscli-bundle.zip

RUN yarn global add @joblocal/aws-cfn-deployment

WORKDIR /workspace

VOLUME /workspace

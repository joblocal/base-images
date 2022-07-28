FROM golang:1.15-alpine

LABEL maintainer="joblocal GmbH <produktentwicklung@joblocal.de>"

RUN apk add --no-cache --update \
  bash \
  curl \
  git \
  jq \
  python3 \
  zip \
  yarn \
  make \
  gcc \
  python3-dev \
  libffi-dev \
  openssl-dev \
  libc-dev

RUN curl -O https://bootstrap.pypa.io/pip/3.6/get-pip.py \
    && python3 get-pip.py \
    && pip install --upgrade pip \
    && pip install awscli --upgrade \
    && pip install docker-compose --upgrade

RUN yarn global add \
    @joblocal/aws-cfn-deployment \
    serverless


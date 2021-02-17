FROM node:10.16-alpine

LABEL maintainer="joblocal GmbH <produktentwicklung@joblocal.de>"

RUN apk add --no-cache --update \
  bash \
  curl \
  jq \
  python3 \
  zip \
  imagemagick

RUN curl -O https://bootstrap.pypa.io/get-pip.py \
    && python3 get-pip.py \
    && pip install --upgrade pip \
    && pip install awscli --upgrade

RUN yarn global add @joblocal/aws-cfn-deployment \
    && yarn cache clean

FROM node:16.16-alpine3.16

LABEL maintainer="joblocal GmbH <produktentwicklung@joblocal.de>"

RUN apk add --no-cache --update \
  bash \
  curl \
  git \
  jq \
  python3 \
  zip

RUN curl -O https://bootstrap.pypa.io/get-pip.py \
    && python3 get-pip.py \
    && pip install --upgrade pip \
    && pip install awscli --upgrade

RUN yarn global add \
    @joblocal/aws-cfn-deployment \
    sass \
    && yarn cache clean

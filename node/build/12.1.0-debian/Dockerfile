FROM node:12.1.0

LABEL maintainer="joblocal GmbH <produktentwicklung@joblocal.de>"

RUN apt-get update && apt-get install -y \
  bash \
  curl \
  git \
  jq \
  python3 \
  zip \
  && rm -rf /var/lib/apt/lists/*

RUN curl -O https://bootstrap.pypa.io/pip/3.5/get-pip.py \
    && python3 get-pip.py \
    && pip install --upgrade pip \
    && pip install awscli --upgrade

RUN yarn global add \
    @joblocal/aws-cfn-deployment \
    sass \
    && yarn cache clean

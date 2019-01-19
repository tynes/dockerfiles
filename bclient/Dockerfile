FROM node:alpine AS base

RUN mkdir /opt/bclient
WORKDIR /opt/bclient

ARG GIT_REPO=https://github.com/bcoin-org/bclient.git
ARG BRANCH=master

RUN apk upgrade --no-cache \
  && apk add --no-cache bash git

RUN git clone $GIT_REPO /opt/bclient \
  && git checkout $BRANCH

RUN npm install

ENV PATH="${PATH}:/opt/bclient/bin:/opt/bclient/node_modules/.bin"

CMD ["bash"]

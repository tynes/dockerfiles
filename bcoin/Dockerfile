FROM node:alpine AS base

CMD bcoin

RUN mkdir /opt/bcoin
WORKDIR /opt/bcoin

ARG GIT_REPO=https://github.com/bcoin-org/bcoin.git
ARG BRANCH=master

RUN apk upgrade --no-cache \
  && apk add --no-cache bash git

RUN git clone $GIT_REPO /opt/bcoin \
  && git checkout $BRANCH

FROM base AS build

RUN apk add --no-cache g++ gcc make python2
RUN npm install --production

FROM base
ENV PATH="${PATH}:/opt/bcoin/bin:/opt/bcoin/node_modules/.bin"
COPY --from=build /opt/bcoin /opt/bcoin/

EXPOSE 8334 8333 8332 18334 18333 18332

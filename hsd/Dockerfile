FROM node:10-alpine AS base

RUN mkdir /opt/hsd
WORKDIR /opt/hsd

# dynamically linked deps
RUN apk upgrade --no-cache \
  && apk add --no-cache unbound-dev

FROM base AS build

ARG GIT_REPO=https://github.com/handshake-org/hsd.git
ARG BRANCH=master

# build deps
RUN apk upgrade --no-cache \
  && apk add --no-cache bash \
  git python2 g++ gcc make

RUN git clone $GIT_REPO /opt/hsd \
  && git checkout $BRANCH

RUN npm install

FROM base

CMD hsd 

ENV PATH="${PATH}:/opt/hsd/bin:/opt/hsd/node_modules/.bin"
COPY --from=build /opt/hsd/ /opt/hsd/

# main testnet regtest simnet
EXPOSE 12038 13038 14038 15038

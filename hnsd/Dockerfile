FROM alpine:latest AS base

# Install dynamically linked libraries
RUN apk upgrade --no-cache \
  && apk add --no-cache unbound-dev

FROM base AS build

RUN mkdir /opt/hnsd
WORKDIR /opt/hnsd

ARG GIT_REPO=https://github.com/handshake-org/hnsd.git
ARG BRANCH=master
ARG NETWORK=testnet

# Install build tools
RUN apk upgrade --no-cache \
  && apk add --no-cache bash git automake libtool autoconf build-base

RUN git clone $GIT_REPO /opt/hnsd \
  && git checkout $BRANCH

RUN ./autogen.sh && ./configure --with-network=$NETWORK && make

FROM base

ENTRYPOINT ["hnsd"]

COPY --from=build /opt/hnsd/hnsd /usr/bin/hnsd

# default root ns and recursive ns ports
EXPOSE 15359 15360

# main testnet regtest simnet
EXPOSE 12038 13038 14038 15038

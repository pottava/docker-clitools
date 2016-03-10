# jq v1.5

FROM alpine:3.3

ENV GLIBC_VERSION=2.21-r2 \
    JQ_VERSION=1.5

RUN apk --no-cache add --virtual build-dependencies curl make gcc g++ \
      && mkdir -p /tmp/src \
      && cd /tmp/src \
      && ALPINE_GLIBC_BASE_URL="https://circle-artifacts.com/gh/andyshinn/alpine-pkg-glibc/6/artifacts/0/home/ubuntu/alpine-pkg-glibc/packages/x86_64" \
      && curl --location --show-error -O ${ALPINE_GLIBC_BASE_URL}/glibc-${GLIBC_VERSION}.apk \
      && curl --location --show-error -O ${ALPINE_GLIBC_BASE_URL}/glibc-bin-${GLIBC_VERSION}.apk \
      && apk --no-cache add --allow-untrusted glibc-${GLIBC_VERSION}.apk glibc-bin-${GLIBC_VERSION}.apk \
      && /usr/glibc/usr/bin/ldconfig /lib /usr/glibc/usr/lib \
      && curl --location --show-error -O https://github.com/stedolan/jq/releases/download/jq-${JQ_VERSION}/jq-${JQ_VERSION}.tar.gz \
      && tar xvzf jq-${JQ_VERSION}.tar.gz \
      && cd jq-${JQ_VERSION} \
      && ./configure \
      && make \
      && make install \
      && rm -rf /tmp/* \
      && apk del --purge build-dependencies

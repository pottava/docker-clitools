# jo v0.7

FROM alpine:3.3

ENV GLIBC_VERSION=2.21-r2 \
    JO_VERSION=0.7

RUN apk --no-cache add --virtual build-dependencies curl make automake autoconf gcc g++ \
      && mkdir -p /tmp/src \
      && cd /tmp/src \
      && ALPINE_GLIBC_BASE_URL="https://circle-artifacts.com/gh/andyshinn/alpine-pkg-glibc/6/artifacts/0/home/ubuntu/alpine-pkg-glibc/packages/x86_64" \
      && curl --location --show-error -O ${ALPINE_GLIBC_BASE_URL}/glibc-${GLIBC_VERSION}.apk \
      && curl --location --show-error -O ${ALPINE_GLIBC_BASE_URL}/glibc-bin-${GLIBC_VERSION}.apk \
      && apk --no-cache add --allow-untrusted glibc-${GLIBC_VERSION}.apk glibc-bin-${GLIBC_VERSION}.apk \
      && /usr/glibc/usr/bin/ldconfig /lib /usr/glibc/usr/lib \
      && curl --location --show-error -O https://github.com/jpmens/jo/archive/v${JO_VERSION}.tar.gz \
      && tar xvzf v${JO_VERSION}.tar.gz \
      && cd jo-${JO_VERSION} \
      && autoreconf -i \
      && ./configure \
      && make \
      && make install \
      && rm -rf /tmp/* \
      && apk del --purge build-dependencies

ENTRYPOINT ["/usr/local/bin/jo"]

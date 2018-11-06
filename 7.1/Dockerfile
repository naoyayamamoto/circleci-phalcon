FROM circleci/php:7.1

LABEL maintainer="naoyayamamoto <github.com/naoyayamamoto>"

ARG PHALCON_VERSION=3.4.1
ARG PHALCON_EXT_PATH=php7/64bits

USER root

RUN set -xe && \
        # Compile Phalcon
        curl -LO https://github.com/phalcon/cphalcon/archive/v${PHALCON_VERSION}.tar.gz && \
        tar xzf ${PWD}/v${PHALCON_VERSION}.tar.gz && \
        docker-php-ext-install -j $(getconf _NPROCESSORS_ONLN) ${PWD}/cphalcon-${PHALCON_VERSION}/build/${PHALCON_EXT_PATH} && \
        # Remove all temp files
        rm -r \
            ${PWD}/v${PHALCON_VERSION}.tar.gz \
            ${PWD}/cphalcon-${PHALCON_VERSION}

COPY docker-phalcon-* /usr/local/bin/

USER circleci

CMD ["/bin/sh"]
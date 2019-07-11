FROM php:7.1-cli

ARG HTTP_PROXY
ARG HTTPS_PROXY
ARG NO_PROXY

ENV DEBIAN_FRONTEND=noninteractive

RUN \
    echo "Install base packages" \
    && ([ -z "$HTTP_PROXY" ] || echo "Acquire::http::Proxy \"${HTTP_PROXY}\";" > /etc/apt/apt.conf.d/99HttpProxy) \
    && apt-get update \
    && apt-get install -y --no-install-recommends git zip unzip

RUN curl -x "$HTTP_PROXY" --silent --show-error https://getcomposer.org/installer | php -- --install-dir /usr/local/bin --filename composer

WORKDIR /var/project

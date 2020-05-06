FROM alpine:3.8

RUN apk upgrade
RUN apk --update \
    add alpine-sdk \
    nodejs \
    nodejs-npm \
    xvfb \
    chromium \
    bzip2 \
    curl \
    bash \
    python \
    python-dev \
    py-setuptools \
    build-base \
    libressl-dev \
    libffi-dev \
    py-pip \
    unzip

RUN set -x \
    && apk add  --no-cache --repository http://dl-cdn.alpinelinux.org/alpine/v3.7/main/ nodejs=8.9.3-r1 \
    && rm -rf /var/lib/apk/lists/* /tmp/* /var/tmp/* \
    && pip install --upgrade pip \
    && pip install ansible boto boto3 awscli

ADD scripts/xvfb-chrome /usr/bin/xvfb-chrome
RUN ln -sf /usr/bin/xvfb-chrome /usr/bin/google-chrome \
    && npm install -g @angular/cli --unsafe-perm \
    && npm install -g istanbul \
    && npm install -g jasmine-node \
    && npm install -g jasmine-core@* \
    && npm install -g karma \
    && npm install -g karma-coverage-istanbul-reporter \
    && npm install -g karma-jasmine-html-reporter \
    && npm install -g karma-chrome-launcher \
    && npm install -g karma-jasmine \
    && npm install -g typescript

ENV CHROME_BIN /usr/bin/google-chrome

USER root

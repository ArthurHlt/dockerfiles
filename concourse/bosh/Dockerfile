FROM ruby:2.2-alpine

ENV CF_CLI_VERSION "6.26.0"

ENV SPRUCE_VERSION 1.8.9

ENV spiff_version="1.0.7"

RUN gem install bosh_cli -v 1.3232.0 --no-rdoc --no-ri

RUN curl -L "https://cli.run.pivotal.io/stable?release=linux64-binary&version=${CF_CLI_VERSION}" | tar -zx -C /usr/local/bin

RUN curl -L 'https://github.com/stedolan/jq/releases/download/jq-1.5/jq-linux64' -o /usr/local/bin/jq && chmod +x /usr/local/bin/jq

RUN apk add --update wget ca-certificates \
  && wget https://github.com/geofffranks/spruce/releases/download/v${SPRUCE_VERSION}/spruce-linux-amd64 \
  && chmod +x spruce-linux-amd64 \
  && mv spruce-linux-amd64 /usr/local/bin/spruce \
  && apk del wget ca-certificates \
  && rm -rf /var/cache/apk/*

RUN wget -O /tmp/spiff_linux_amd64.zip "https://github.com/cloudfoundry-incubator/spiff/releases/download/v${spiff_version}/spiff_linux_amd64.zip" && \
    unzip /tmp/spiff_linux_amd64.zip -d /usr/local/bin && \
    chmod 755 /usr/local/bin/spiff && \
    rm /tmp/spiff_linux_amd64.zip

RUN apk add --update bash openssl openssh-client file git && rm -rf /var/cache/apk/*
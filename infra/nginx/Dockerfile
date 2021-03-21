FROM node:14.2-alpine as node
FROM nginx:1.18-alpine
LABEL maintainer="sorinaji <hello@sori883.com>"
SHELL ["/bin/ash", "-oeux", "pipefail", "-c"]

ENV TZ=Asia/Tokyo \
 LANG=ja_JP.utf8

RUN apk update && \
  apk add --update --no-cache --virtual=.build-dependencies g++

# node command
COPY --from=node /usr/local/bin /usr/local/bin
# npm command
COPY --from=node /usr/local/lib /usr/local/lib
# nginx config file
COPY ./infra/nginx/default.conf /etc/nginx/conf.d/default.conf

WORKDIR /work/backend
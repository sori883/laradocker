FROM postgres:12
LABEL maintainer="sorinaji <hello@sori883.com>"

ARG DB_USER=phper \
 DB_NAME=laravel_local

ENV TZ=Asia/Tokyo \
 DB_USER=$DB_USER \
 DB_NAME=$DB_NAME \
 LANG=ja_JP.utf8

RUN localedef -i ja_JP -c -f UTF-8 -A /usr/share/locale/locale.alias ja_JP.UTF-8

COPY ./infra/postgresql/docker-entrypoint-initdb.d/ /docker-entrypoint-initdb.d/
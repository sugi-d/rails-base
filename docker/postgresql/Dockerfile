FROM postgres:11.1-alpine

RUN apk add --no-cache tzdata
RUN cp /usr/share/zoneinfo/Asia/Tokyo /etc/localtime
ENV TZ Asia/Tokyo

COPY ./docker/postgresql/initdb.d/* /docker-entrypoint-initdb.d/

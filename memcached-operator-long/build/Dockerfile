FROM alpine:3.8

RUN apk upgrade --update --no-cache

USER nobody

ADD build/_output/bin/memcached-operator-long /usr/local/bin/memcached-operator-long

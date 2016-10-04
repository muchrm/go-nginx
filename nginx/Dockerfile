FROM nginx:alpine

ADD nginx.conf /etc/nginx/
ADD web.conf /etc/nginx/conf.d/web.conf

ARG GO_UPSTREAM=golang

RUN apk update \
    && apk upgrade \
    && apk add --no-cache bash \
    && adduser -D -H -u 1000 -s /bin/bash www-data \
    && rm /etc/nginx/conf.d/default.conf \
    && echo "upstream go-upstream { server ${GO_UPSTREAM}:8080; }" > /etc/nginx/conf.d/upstream.conf

CMD ["nginx", "-g", "daemon off;"]

EXPOSE 80 443
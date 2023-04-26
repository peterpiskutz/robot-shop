FROM alpine AS build
ARG KEY

WORKDIR /instana

RUN apk add --update --no-cache wget

ENV ARTI_PATH='artifact-public.instana.io/artifactory/shared/com/instana/nginx_tracing/'

FROM nginx:1.21.6

EXPOSE 8080

ENV CATALOGUE_HOST=catalogue \
    USER_HOST=user \
    CART_HOST=cart \
    SHIPPING_HOST=shipping \
    PAYMENT_HOST=payment \
    RATINGS_HOST=ratings \
    INSTANA_SERVICE_NAME=nginx-web

COPY entrypoint.sh /root/
ENTRYPOINT ["/root/entrypoint.sh"]

COPY default.conf.template /etc/nginx/conf.d/default.conf.template
COPY static /usr/share/nginx/html

FROM ubuntu:latest as building
WORKDIR /building
COPY docker-install-redis-ssl.sh .
RUN apt update && ./docker-install-redis-ssl.sh

FROM ubuntu:latest
MAINTAINER botv96@gmail.com
LABEL Description="Run SSL with Redis"
WORKDIR /opt/redis

COPY --from=building /building/redis .
COPY --from=building /usr/include/openssl/* /usr/include/openssl/
COPY docker-entrypoint.sh /entrypoint.sh

ENTRYPOINT ["/entrypoint.sh"]
EXPOSE 6379
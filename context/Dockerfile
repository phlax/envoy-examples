ARG BUILD_FROM=docker:dind

FROM $BUILD_FROM

RUN addgroup docker \
	&& adduser envoydev -D -G docker
RUN apk add bash curl docker-compose git jq redis
WORKDIR /home/envoydev

COPY ./run-envoy-example-tests /usr/local/bin

HEALTHCHECK --interval=10s --timeout=5s --retries=20 \
        CMD find /var/run/docker.sock -type s | grep docker.sock

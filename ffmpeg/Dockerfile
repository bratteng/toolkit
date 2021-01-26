FROM alpine:3.13
LABEL org.opencontainers.image.source https://github.com/bratteng/docker-toolkit

WORKDIR /tmp/ffmpeg

RUN set -xe; \
	apk update \
	&& apk add ffmpeg \
	&& rm -rf /var/cache/apk/*

ENTRYPOINT ["ffmpeg"]

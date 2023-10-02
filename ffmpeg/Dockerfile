FROM alpine:3.18.4
LABEL org.opencontainers.image.source https://github.com/bratteng/docker-toolkit

WORKDIR /tmp/ffmpeg

RUN apk add --no-cache ffmpeg

ENTRYPOINT ["ffmpeg"]

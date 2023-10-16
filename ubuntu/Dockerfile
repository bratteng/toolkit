FROM ubuntu:jammy-20231004

RUN apt-get update \
  && apt-get install --no-install-recommends --no-install-suggests -y \
    ca-certificates \
    curl \
    dnsutils \
    iputils-ping \
    iproute2 \
    wget

COPY --from=smallstep/step-cli:0.25.0 /usr/local/bin/step /usr/local/bin/step

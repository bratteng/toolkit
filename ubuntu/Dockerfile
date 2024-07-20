FROM ubuntu@sha256:e3f92abc0967a6c19d0dfa2d55838833e947b9d74edbcb0113e48535ad4be12a

RUN --mount=target=/var/cache/apt/archives,type=cache,sharing=locked \
    apt-get update \
    && apt-get install --no-install-recommends --no-install-suggests -y \
        ca-certificates \
        curl \
        git \
        rsync \
        sudo \
        dnsutils \
        iputils-ping \
        iproute2 \
        wget \
        zsh \
        btop

RUN --mount=target=/var/cache/apt/archives,type=cache,sharing=locked \
        set -xe \
        && git clone --depth=1 https://github.com/omBratteng/dotfiles.git /root/.dotfiles \
        && /root/.dotfiles/bootstrap.sh -f

RUN set -xe \
        && ${HOME}/.oh-my-zsh/custom/themes/powerlevel10k/gitstatus/install \
        && mkdir -p ${HOME}/.oh-my-zsh/cache/completions

COPY --from=redis:7.2.4 /usr/local/bin/redis-cli /usr/local/bin/redis-cli
COPY --from=redis:7.2.4 /usr/local/bin/redis-benchmark /usr/local/bin/redis-benchmark

CMD ["/usr/bin/zsh"]

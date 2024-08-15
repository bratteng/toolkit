FROM quay.io/fedora/fedora:42

RUN --mount=target=/var/cache/dnf,type=cache,sharing=locked \
    dnf update -y \
    && dnf install -y \
        ca-certificates \
        curl \
        bind-utils \
        iputils \
        iproute \
        wget \
        btop \
        git \
        zsh \
        rsync \
        hostname \
        procps \
        vim

RUN --mount=target=/var/cache/dnf,type=cache,sharing=locked \
    set -xe \
    && git clone --depth=1 https://github.com/omBratteng/dotfiles.git /root/.dotfiles \
    && /root/.dotfiles/bootstrap.sh -f

RUN set -xe \
    && ${HOME}/.oh-my-zsh/custom/themes/powerlevel10k/gitstatus/install \
    && mkdir -p ${HOME}/.oh-my-zsh/cache/completions

COPY --from=redis:7.2.5 /usr/local/bin/redis-cli /usr/local/bin/redis-cli
COPY --from=redis:7.2.5 /usr/local/bin/redis-benchmark /usr/local/bin/redis-benchmark

CMD ["/usr/bin/zsh"]

FROM quay.io/fedora/fedora@sha256:d7ebb97fcebff77660250b7ee42c8afbe6d821428bce19775cd78122761aecef

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

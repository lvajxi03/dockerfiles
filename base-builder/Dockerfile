FROM debian:bookworm-slim

RUN apt-get update && apt-get install -y --no-install-recommends \
    ca-certificates \
    curl \
    wget \
    git \
    openssh-client \
    bash \
    make \
    jq \
    yq \
    tar \
    gzip \
    xz-utils \
    unzip \
    zip \
    rsync \
    file \
    procps \
    iputils-ping \
    dnsutils \
    && rm -rf /var/lib/apt/lists/*

RUN useradd -m -u 1000 builder

USER builder
WORKDIR /workspace

CMD ["sleep", "infinity"]


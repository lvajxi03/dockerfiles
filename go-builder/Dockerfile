FROM golang:1.26-bookworm

RUN apt-get update && apt-get install -y --no-install-recommends \
    git \
    openssh-client \
    ca-certificates \
    curl \
    wget \
    jq \
    make \
    rsync \
    && rm -rf /var/lib/apt/lists/*

RUN update-ca-certificates

USER root

WORKDIR /workspace

RUN go version

CMD ["sleep", "infinity"]


# ci-toolbox Dockerfile
# Generate image for hatamoto (executed by kaniko)

FROM debian:bookworm-slim

# ---- system tools ----
RUN apt update && apt install -y \
    git \
    curl \
    ca-certificates \
    ansible \
    openssh-client \
 && rm -rf /var/lib/apt/lists/*

# ---- PEP 668 SAFE MODE (kluczowe) ----
# pozwala pip działać systemowo, ale świadomie

# ---- Hugo ----
ARG HUGO_VERSION=0.159.2

RUN curl -L -o /tmp/hugo.tar.gz \
    https://github.com/gohugoio/hugo/releases/download/v${HUGO_VERSION}/hugo_extended_${HUGO_VERSION}_linux-arm64.tar.gz \
 && tar -xzf /tmp/hugo.tar.gz \
 && mv hugo /usr/local/bin/hugo \
 && chmod +x /usr/local/bin/hugo \
 && rm -rf /tmp/hugo.tar.gz

WORKDIR /workspace


# ci-toolbox Dockerfile
# Generate image for hatamoto (executed by kaniko)

FROM debian:bookworm-slim

RUN apt update && apt install -y \
    git curl python3 python3-pip ca-certificates \
 && pip3 install ansible

ARG HUGO_VERSION=0.159.2

# Hugo needs to be downloaded manually:
RUN curl -L -o /tmp/hugo.tar.gz \
    https://github.com/gohugoio/hugo/releases/download/v${HUGO_VERSION}/hugo_extended_${HUGO_VERSION}_linux-arm64.tar.gz \
 && tar -xzf /tmp/hugo.tar.gz -C /usr/local/bin \
 && chmod +x /usr/local/bin/hugo \
 && rm -rf /tmp/hugo.tar.gz

WORKDIR /workspace


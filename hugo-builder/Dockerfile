FROM registry.lab.local/base-builder:0.1

USER root

ARG HUGO_VERSION=0.161.1

RUN curl -fsSL -o /tmp/hugo.tar.gz \
    "https://github.com/gohugoio/hugo/releases/download/v${HUGO_VERSION}/hugo_extended_${HUGO_VERSION}_linux-arm64.tar.gz" \
    && tar -C /usr/local/bin -xzf /tmp/hugo.tar.gz hugo \
    && chmod +x /usr/local/bin/hugo \
    && rm /tmp/hugo.tar.gz

USER builder
WORKDIR /workspace

CMD ["sleep", "infinity"]

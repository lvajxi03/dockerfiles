FROM quay.io/buildah/stable:v1.43.1

USER root

RUN dnf install -y \
    git \
    bash \
    coreutils \
    ca-certificates \
    curl \
    jq \
    && dnf clean all

WORKDIR /workspace

CMD ["sleep", "infinity"]

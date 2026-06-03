FROM registry.lab.local/base-builder:0.1

USER root

RUN apt-get update && apt-get install -y --no-install-recommends \
    ansible \
    openssh-client \
    rsync \
    python3 \
    python3-pip \
    python3-venv \
    && rm -rf /var/lib/apt/lists/*

RUN mkdir -p /home/builder/.ssh \
    && chown -R builder:builder /home/builder/.ssh \
    && chmod 700 /home/builder/.ssh

USER builder
WORKDIR /workspace

CMD ["sleep", "infinity"]

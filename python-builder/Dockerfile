FROM registry.lab.local/base-builder:0.1

USER root


RUN apt-get update && apt-get install -y --no-install-recommends \
    python3 \
    python3-pip \
    python3-venv \
    python3-build \
    && rm -rf /var/lib/apt/lists/*

RUN python3 -m pip install --break-system-packages \
    build \
    twine \
    wheel \
    setuptools \
    pytest \
    ruff

USER builder
WORKDIR /workspace

CMD ["sleep", "infinity"]

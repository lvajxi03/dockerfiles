FROM gcr.io/kaniko-project/executor:latest AS kaniko

FROM alpine:3.21

RUN apk add --no-cache \
    ca-certificates \
    bash \
    coreutils \
    curl \
    git

COPY --from=kaniko /kaniko /kaniko

ENV PATH="/kaniko:${PATH}"

WORKDIR /workspace

CMD ["sleep", "infinity"]


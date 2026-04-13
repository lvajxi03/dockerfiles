FROM jenkins/jenkins:lts

USER root

# kubectl:
RUN apt update && apt install -y curl \
 && curl -LO "https://dl.k8s.io/release/v1.29.0/bin/linux/arm64/kubectl" \
 && install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl \
 && rm kubectl

# Jenkins plugins:
RUN jenkins-plugin-cli --plugins \
    kubernetes \
    workflow-job \
    workflow-aggregator \
    git \
    remoting

USER jenkins


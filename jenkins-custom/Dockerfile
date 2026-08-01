FROM jenkins/jenkins:lts-jdk21 AS jenkins-tools

FROM eclipse-temurin:21-jre-jammy

ARG JENKINS_VERSION=2.568.1

USER root

RUN apt-get update && apt-get install -y --no-install-recommends \
    curl \
    git \
    openssh-client \
    ca-certificates \
    tini \
    fontconfig \
    jq \
    unzip \
    zip \
    && rm -rf /var/lib/apt/lists/*

RUN useradd -m -d /var/jenkins_home -u 1000 jenkins

RUN mkdir -p /usr/share/jenkins /var/jenkins_home /usr/share/jenkins/ref/plugins

RUN curl -fsSL \
    -o /usr/share/jenkins/jenkins.war \
    "https://get.jenkins.io/war-stable/${JENKINS_VERSION}/jenkins.war"

COPY --from=jenkins-tools /usr/bin/jenkins-plugin-cli /usr/bin/jenkins-plugin-cli
COPY --from=jenkins-tools /opt/jenkins-plugin-manager.jar /opt/jenkins-plugin-manager.jar

COPY plugins.txt /tmp/plugins.txt

COPY plugins.txt /tmp/plugins.txt

RUN JENKINS_WAR=/usr/share/jenkins/jenkins.war \
    JENKINS_HOME=/usr/share/jenkins/ref \
    jenkins-plugin-cli \
      --war /usr/share/jenkins/jenkins.war \
      --plugin-file /tmp/plugins.txt

RUN chown -R jenkins:jenkins /usr/share/jenkins /var/jenkins_home

USER jenkins

ENV JENKINS_HOME=/var/jenkins_home

VOLUME /var/jenkins_home

EXPOSE 8080 50000

ENTRYPOINT ["/usr/bin/tini", "--"]
CMD ["java", "-Djenkins.install.runSetupWizard=false", "-jar", "/usr/share/jenkins/jenkins.war", "--httpPort=8080"]


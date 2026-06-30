FROM eclipse-temurin:21-jre-jammy

ARG JENKINS_VERSION=2.516.1

RUN apt-get update && apt-get install -y --no-install-recommends \
    curl \
    git \
    openssh-client \
    ca-certificates \
    tini \
    fontconfig \
    && rm -rf /var/lib/apt/lists/*

RUN useradd -m -d /var/jenkins_home -u 1000 jenkins

RUN mkdir -p /usr/share/jenkins /var/jenkins_home \
    && curl -fsSL \
      -o /usr/share/jenkins/jenkins.war \
      "https://get.jenkins.io/war-stable/${JENKINS_VERSION}/jenkins.war" \
    && chown -R jenkins:jenkins /usr/share/jenkins /var/jenkins_home

USER jenkins

ENV JENKINS_HOME=/var/jenkins_home
ENV JAVA_OPTS="-Djenkins.install.runSetupWizard=false"

VOLUME /var/jenkins_home

EXPOSE 8080 50000

ENTRYPOINT ["/usr/bin/tini", "--"]
CMD ["java", "-jar", "/usr/share/jenkins/jenkins.war", "--httpPort=8080"]


FROM jenkins/jenkins:alpine

USER root

RUN apk add --no-cache \
    openjdk11 \
    bash \
    docker \
    curl \
    unzip \
    openrc

# Define Gradle environment variables
ENV GRADLE_VERSION=7.6 \
    GRADLE_HOME=/opt/gradle/gradle-7.6 \
    PATH=/opt/gradle/gradle-7.6/bin:$PATH

# Install Gradle and verify
RUN mkdir -p /opt/gradle && \
    curl -fsSL https://services.gradle.org/distributions/gradle-${GRADLE_VERSION}-bin.zip -o /tmp/gradle.zip && \
    unzip /tmp/gradle.zip -d /opt/gradle && \
    rm /tmp/gradle.zip && \
    /opt/gradle/gradle-${GRADLE_VERSION}/bin/gradle -v

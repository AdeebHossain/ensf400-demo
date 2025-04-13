FROM jenkins/jenkins:alpine

# Switch to root user
USER root

# Install necessary packages in one step to reduce layers and image size
RUN apk add --no-cache \
    openjdk11 \
    bash \
    docker \
    curl \
    unzip \
    openrc

# Set environment variables for Gradle
ENV GRADLE_VERSION=7.6 \
    GRADLE_HOME=/opt/gradle \
    PATH=/opt/gradle/gradle-${GRADLE_VERSION}/bin:$PATH

# Download and install Gradle
RUN mkdir -p ${GRADLE_HOME} && \
    curl -fsSL https://services.gradle.org/distributions/gradle-${GRADLE_VERSION}-bin.zip -o /tmp/gradle.zip && \
    unzip /tmp/gradle.zip -d ${GRADLE_HOME} && \
    rm /tmp/gradle.zip

# Verify Gradle installation
RUN gradle -v

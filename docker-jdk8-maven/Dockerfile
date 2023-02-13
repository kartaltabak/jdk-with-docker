FROM kartaltabak/jdk-with-docker:jdk8

ARG USERNAME=jenkins
ARG HOME_DIR=/home/$USERNAME

ARG MAVEN_VERSION=3.9.0
ARG BASE_URL=https://apache.osuosl.org/maven/maven-3/${MAVEN_VERSION}/binaries

USER root

RUN mkdir -p /usr/share/maven \
  && curl -fsSL -o /tmp/apache-maven.tar.gz ${BASE_URL}/apache-maven-${MAVEN_VERSION}-bin.tar.gz \
  && tar -xzf /tmp/apache-maven.tar.gz -C /usr/share/maven --strip-components=1 \
  && rm -f /tmp/apache-maven.tar.gz \
  && ln -s /usr/share/maven/bin/mvn /usr/bin/mvn

ENV MAVEN_HOME /usr/share/maven
ENV MAVEN_CONFIG "${HOME_DIR}/.m2"

USER ${USERNAME}

RUN mkdir -p ${MAVEN_CONFIG}

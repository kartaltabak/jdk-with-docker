FROM openjdk:21-jdk

ARG USERNAME=jenkins
ARG UID=1000
ARG GID=1000
ARG DOCKER_GID=1001

RUN groupadd --gid $GID $USERNAME

ARG HOME_DIR=/home/$USERNAME

RUN useradd --home-dir  $HOME_DIR --create-home --shell /bin/bash --uid $UID --gid ${USERNAME} ${USERNAME}

RUN groupadd -g ${DOCKER_GID} docker

RUN microdnf install -y yum-utils && \
    yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo && \
    microdnf install -y docker-ce --nobest && \
    usermod -aG docker $USERNAME

RUN mkdir -p /var/${USERNAME}_home && \
    chown ${USERNAME}:${USERNAME} /var/${USERNAME}_home

USER $USERNAME

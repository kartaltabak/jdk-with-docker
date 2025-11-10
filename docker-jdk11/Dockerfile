FROM eclipse-temurin:11-jdk

ARG USERNAME=ubuntu
ARG DOCKER_GID=1001

ARG DEBIAN_FRONTEND=noninteractive

RUN apt-get update \
    && apt-get -y install \
    software-properties-common

RUN groupadd -g ${DOCKER_GID} docker

RUN (curl -fsSL https://download.docker.com/linux/ubuntu/gpg | \
     apt-key --keyring /etc/apt/trusted.gpg.d/docker-apt-key.gpg add ) \
    && add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/debian stretch stable" \
    && apt-get update \
    && apt-get -y install docker-ce \
    && usermod -aG docker $USERNAME

USER $USERNAME

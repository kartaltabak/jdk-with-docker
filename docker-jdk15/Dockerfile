FROM openjdk:15-jdk

ARG USERNAME=jenkins
ARG UID=1000
ARG GID=1000
ARG DOCKER_GID=1001

RUN groupadd --gid $GID $USERNAME

ARG HOME_DIR=/home/$USERNAME

RUN useradd --home-dir  $HOME_DIR --create-home --shell /bin/bash --uid $UID --gid ${USERNAME} ${USERNAME}

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

RUN mkdir -p /var/${USERNAME}_home && \
    chown ${USERNAME}:${USERNAME} /var/${USERNAME}_home

USER $USERNAME

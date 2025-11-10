FROM eclipse-temurin:21-jdk

ARG USERNAME=ubuntu
ARG DOCKER_GID=1001

RUN groupadd -g ${DOCKER_GID} docker

RUN apt-get update && apt-get install -y --no-install-recommends \
      ca-certificates curl gnupg lsb-release && \
    install -m 0755 -d /etc/apt/keyrings && \
    curl -fsSL https://download.docker.com/linux/$(. /etc/os-release; echo $ID)/gpg \
      | gpg --dearmor -o /etc/apt/keyrings/docker.gpg && \
    echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] \
      https://download.docker.com/linux/$(. /etc/os-release; echo $ID) \
      $(. /etc/os-release; echo $VERSION_CODENAME) stable" \
      > /etc/apt/sources.list.d/docker.list && \
    apt-get update && apt-get install -y --no-install-recommends docker-ce-cli

RUN usermod -aG docker ${USERNAME}

USER ${USERNAME}

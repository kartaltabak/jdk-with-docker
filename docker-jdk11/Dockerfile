FROM eclipse-temurin:11-jdk

ARG USERNAME=ubuntu
ARG DOCKER_GID=1001

ARG DEBIAN_FRONTEND=noninteractive

RUN groupadd -g ${DOCKER_GID} docker

RUN  curl -fsSL https://download.docker.com/linux/ubuntu/gpg \
        -o /etc/apt/keyrings/docker.asc \
    && . /etc/os-release \
    && printf '%s\n' \
        "Types: deb" \
        "URIs: https://download.docker.com/linux/ubuntu" \
        "Suites: ${UBUNTU_CODENAME:-$VERSION_CODENAME}" \
        "Components: stable" \
        "Architectures: $(dpkg --print-architecture)" \
        "Signed-By: /etc/apt/keyrings/docker.asc" \
        > /etc/apt/sources.list.d/docker.sources \
    && apt-get update \
    && apt-get -y install docker-ce-cli docker-buildx-plugin docker-compose-plugin

RUN usermod -aG docker "${USERNAME}"

USER "${USERNAME}"

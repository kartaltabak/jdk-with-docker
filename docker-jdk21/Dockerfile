FROM eclipse-temurin:21-jdk

ARG USERNAME=ubuntu
ARG DOCKER_GID=1001

ARG DEBIAN_FRONTEND=noninteractive

RUN groupadd -g ${DOCKER_GID} docker

#RUN apt-get update && apt-get install -y --no-install-recommends \
#      ca-certificates curl gnupg lsb-release && \
#    install -m 0755 -d /etc/apt/keyrings && \
#    curl -fsSL https://download.docker.com/linux/$(. /etc/os-release; echo $ID)/gpg \
#      | gpg --dearmor -o /etc/apt/keyrings/docker.gpg && \
#    echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] \
#      https://download.docker.com/linux/$(. /etc/os-release; echo $ID) \
#      $(. /etc/os-release; echo $VERSION_CODENAME) stable" \
#      > /etc/apt/sources.list.d/docker.list && \
#    apt-get update && apt-get install -y --no-install-recommends docker-ce-cli

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

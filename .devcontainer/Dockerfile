FROM mcr.microsoft.com/devcontainers/base:debian-12

ENV DEBIAN_FRONTEND=noninteractive

SHELL ["/bin/bash", "-c"]

RUN apt update && \
    apt install -y curl && \
    echo 'deb http://download.opensuse.org/repositories/shells:/fish:/release:/3/Debian_12/ /' | tee /etc/apt/sources.list.d/shells:fish:release:3.list && \
    curl -fsSL https://download.opensuse.org/repositories/shells:fish:release:3/Debian_12/Release.key | gpg --dearmor | tee /etc/apt/trusted.gpg.d/shells_fish_release_3.gpg > /dev/null && \
    apt update && \
    apt install -y \
        git \
        xdg-utils \
        fish && \
    apt clean && \
    rm -rf /var/lib/apt/lists/*

USER vscode
WORKDIR /work

RUN curl https://get.volta.sh | bash
ENV PATH="/home/vscode/.volta/bin:${PATH}"
RUN volta install \
    node@22.12.0 \
    npm@11.0.0 \
    sort-package-json@2.12.0 \
    tsx@4.19.2 \
    typescript@5.6.2

RUN echo "alias ll='ls -alF'" >> /home/vscode/.config/fish/config.fish
RUN echo "functions --erase fish_greeting" >> /home/vscode/.config/fish/config.fish

FROM ubuntu:24.04

ARG USERNAME=vscode
ARG USER_UID=1000
ARG USER_GID=1000

ENV DEBIAN_FRONTEND=noninteractive

# Basic packages + Neovim + tmux
RUN apt-get update && apt-get install -y --no-install-recommends \
    ca-certificates curl git sudo unzip \
    neovim tmux fzf ripgrep fd-find bat \
    python3 python3-pip \
    && rm -rf /var/lib/apt/lists/*

# Create the non-root user
RUN groupadd --gid $USER_GID $USERNAME \
    && useradd --uid $USER_UID --gid $USER_GID -m $USERNAME \
    && echo "$USERNAME ALL=(ALL) NOPASSWD:ALL" > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME

# Install mise
RUN curl https://mise.run | MISE_INSTALL_PATH=/usr/local/bin/mise sh

USER $USERNAME
WORKDIR /home/$USERNAME

# Activate mise for the user
RUN echo 'eval "$(mise activate bash)"' >> ~/.bashrc

WORKDIR /workspaces

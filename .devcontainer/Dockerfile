# Use the official Python image
FROM ghcr.io/astral-sh/uv:python3.13-bookworm-slim

# set labels
# LABEL org.opencontainers.image.created=$(date -u +"%Y-%m-%dT%H:%M:%SZ")

# LABEL org.opencontainers.image.created="${BUILD_DATE}"

LABEL maintainer="EED-Solutions"
LABEL org.opencontainers.image.title="eed_docker_python_uv"
LABEL org.opencontainers.image.description="Python 3.13 base image with uv, gh, duckdb and dev tools for CI and Codespaces"
LABEL org.opencontainers.image.source="https://github.com/EED-Solutions/eed_docker_python_uv"
LABEL org.opencontainers.image.licenses="MIT"


# Install system packages:
RUN apt-get update && apt-get install -y \
    curl \
    gnupg \
    git \
    unzip \
    build-essential \
    libsqlite3-dev \
    && rm -rf /var/lib/apt/lists/*
# duckdb
RUN curl -sL https://install.duckdb.org | sh && \
    mkdir -p  /usr/local/bin && \
    cp /root/.duckdb/cli/latest/duckdb /usr/local/bin/duckdb && \
    chmod +x /usr/local/bin/duckdb
# github cli
RUN curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg | \
    gpg --dearmor -o /usr/share/keyrings/githubcli-archive-keyring.gpg && \
    echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | \
    tee /etc/apt/sources.list.d/github-cli.list > /dev/null && \
    apt-get update && apt-get install -y gh

# Install the project into `/workspace`
WORKDIR /workspace


# Create vscode user to satisfy Codespaces requirement
RUN useradd -m vscode
USER vscode

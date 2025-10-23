# --- Java 17 ベース ---
FROM mcr.microsoft.com/devcontainers/java:17

# --- 環境変数 ---
ENV DEBIAN_FRONTEND=noninteractive
ENV SDKMAN_DIR=/root/.sdkman

# --- rootで必要なツールをインストール ---
USER root
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        curl \
        unzip \
        zip \
        git \
        postgresql-client && \
    apt-get clean && rm -rf /var/lib/apt/lists/*

# --- SDKMANをインストール ---
RUN curl -s "https://get.sdkman.io" | bash

# --- Gradleインストール（非対話、自動承認） ---
RUN bash -c "source $SDKMAN_DIR/bin/sdkman-init.sh && yes | sdk install gradle 8.10.2"

# --- 作業ディレクトリ ---
WORKDIR /workspace/backend

# --- デフォルトユーザー ---
USER vscode

# --- bashをデフォルトに変更（必要に応じて） ---
SHELL ["/bin/bash", "-c"]

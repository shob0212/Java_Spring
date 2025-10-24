# Java 17 + Gradle 8.10.2 ベース
# -----------------------------------------
FROM gradle:8.10.2-jdk17

# root 権限で必要なツールをインストール
USER root

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        curl \
        git \
        sudo \
        postgresql-client \
        ca-certificates && \
    # Node.js 18.x の導入（gitmoji用）
    curl -fsSL https://deb.nodesource.com/setup_18.x | bash - && \
    apt-get install -y nodejs && \
    npm install -g gitmoji-cli && \
    apt-get clean && rm -rf /var/lib/apt/lists/* && \
    \
    # vscodeユーザーを作成（VSCode Dev Container 用）
    useradd -m vscode && echo "vscode ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers

# vscodeユーザーに切り替え
USER vscode

# 作業ディレクトリを指定
WORKDIR /workspace

# bash をデフォルトシェルに
SHELL ["/bin/bash", "-c"]

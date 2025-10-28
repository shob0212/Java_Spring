# ...existing code...
FROM gradle:8.10.2-jdk17

# root 権限で必要なツールをインストール
USER root

# ツール類のインストール + Node.js + gitmoji
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
    apt-get clean && rm -rf /var/lib/apt/lists/*

# --- ここから追加: vscode ユーザーを作成 --

# 作業ディレクトリを指定
WORKDIR /workspace

# bash をデフォルトシェルに
SHELL ["/bin/bash", "-c"]
# ...existing code...
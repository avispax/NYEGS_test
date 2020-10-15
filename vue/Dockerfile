FROM node:lts-alpine

# カレントワーキングディレクトリとして 'vue' フォルダを指定する
WORKDIR /app

# プロジェクトの依存ライブラリをインストールする
RUN apk update && \
    npm install -g npm && \
    npm install -g @vue/cli

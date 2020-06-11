FROM node:lts-alpine

# カレントワーキングディレクトリとして 'vue' フォルダを指定する
WORKDIR /usr/src/vue

# `package.json` と `package-lock.json` （あれば）を両方コピーする
#COPY package*.json ./

# プロジェクトの依存ライブラリをインストールする
RUN apk update && \
    npm install && \
    npm install -g npm && \
    npm install -g vue-cli

# カレントワーキングディレクトリ(つまり 'app' フォルダ)にプロジェクトのファイルやフォルダをコピーする
#COPY . .

# 本番向けに圧縮しながらアプリケーションをビルドする
#RUN npm run build

#EXPOSE 9000
#CMD [ "http-server", "dist" ]

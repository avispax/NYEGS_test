FROM node:lts-alpine

# カレントワーキングディレクトリとして 'vue' フォルダを指定する
WORKDIR /usr/src/vue

# `package.json` と `package-lock.json` （あれば）を両方コピーする
#COPY package*.json ./

# プロジェクトの依存ライブラリをインストールする
RUN apk update && \
    npm install && \
    npm install -g npm && \
    npm install -g @vue/cli \
     npm install -D webpack webpack-cli babel-loader @babel/core @babel/preset-env


# カレントワーキングディレクトリ(つまり 'app' フォルダ)にプロジェクトのファイルやフォルダをコピーする
#COPY . .

CMD ["npm" "run" "duild2"]

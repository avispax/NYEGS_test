# NYEGS_test

色々テスト。内容は時期によってめちゃ変わります。

## 0 : 前提

1. windowsはWLS2が必要なので、インストールしておくこと。
2. docker for windows を使うので、これもインストールしておくこと。
3. 適当に自分のプロジェクト用ディレクトリを作ってスタート。自分は「c:\work\myProject」とか適当に。
4. 直下にdocker-compsoe.ymlを作る（gitから落とす）
5. data/www を作る
6. nginxとvueのディレクトリを作る。
7. Dockerfileを入れとく。 

## 1 : 手順書とかそういうの

### 1-1 : ドッカーを動かす。

1. docker-compose build
2. docker-compose up -d
3. docker-compose ps でプロセス確認して、nginxとvueが動いとること。

### 1-2 : vueの初回のみの色々。ここを自動化できないんだろうか。

プロセスの中にvueを作り出す必要あり。  
プロセスの状況はGitとかで共有するものではないので、各自の環境でcreateとかしないといけないザマス。  
以下を実行する。

1. プロセスに入る
    > docker exec -it vue sh

    ちなみにここからLinux環境なのでただLinuxで遊ぶ実験とかしてもよいよ。lsとか。

2. vue のインスタンス？スケルトン（昭和用語）？を作り出す。
    > vue create my-test

    * vue createとvue init の違いは？ createのほうが公式にも採用されてる=推奨されてるっぽいから、そっちで。

    * 名前は適当。（my-test）
    * Vue2とVue3（お試し版）どっち？ どうせ将来はVue3（正式版）が出るから、いまはどっちでもいいよ。どうせ作り直す環境です。
    * yarmとnpmどっち。まじでどっちでもいいからnpmとかしとけ。僕の趣味。
    * 他あれば適当。時期によって変わるんだよねここ。
    * ちなみに /app 配下でやりなされ。/app/my-test ってなるはずだから。

3. とりあえずビルドしておく
    > cd my-test
    > npm run build

    dist とか新ディレクトリができるよ。

4. コンテナから出る。
    > exit
    これで、自分のdata/www/my-testとかがコンテナとの同期（volumesのところ）により色々と生成されているのがわかりますでしょうよ。

## 1-3 : nginx側を調整する。

1. とりあえずnginxに入る。
    > docker-compose exec nginx /bin/bash

2. めんどいのでコンフィグを直接変更する。めんどいから。
    - /etc/nginx/conf.d/default.conf ← たぶんこいつ。
    - root を docker-composeとかで指定している「/var/www/html」これに。

3. 適当に再起動する。

4. 確認する。
    - localhost:9000

## 99-1 : 自分用docker-composeコマンド

1. ```docker-compose build``` : これでdocker-composeの内容をイメージ作成します
2. ```docker-compose up -d``` : 〃、イメージをアップロードします（Dockerに登録 → 仮想環境にpushみたいなもの）
3. ```docker-compose stop```

## 99-2 : 自分用（略）その2

1. ```docker-compose ps``` : Docker内のイメージとか、いまどんな状態？ 何が乗っかっているか、それは動いているのか、など。
2. ```docker-compose ps --service```
3. ```docker-compose exec nginx /bin/bash``` : 中に入った。これはnginxの例。


## 99-3 : いまの内容

1. まずは上記手順で実施。
自分にしかわからない手順になっちゃってるので、公開はできない。
とりあえずVueは起動する。
というか、これはVueをプロセスでcreateして、できたものをnginxの中に配布しているだけだな。
なんかこう、プロセス連携してるわけではないらしい。
それは狙ったものか？ 違う気がする。
というか、そうなるとVueとは。って気がする。

2. 端末を変えてやってみた。
distまでGithubに載せてるんだけど、なぜかDLされなかった。不思議。
というわけで、VueのプロセスでCreateからやり直した。
nginx側はプロセス内のdefault.confを編集しているので、Github上にはない。
なのでその部分の手順から再実施する必要あり。

けっきょく、この手順とGithubはあんまりダメだなー。もっと自動化せねば。


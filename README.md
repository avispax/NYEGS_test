# NYEGS_test

色々テスト。内容は時期によってめちゃ変わります。

## 自分用docker-composeコマンド

1. ```docker-compose build``` : これでdocker-composeの内容をイメージ作成します
2. ```docker-compose up -d``` : 〃、イメージをアップロードします（Dockerに登録 → 仮想環境にpushみたいなもの）
3. ```docker-compose stop```

## 自分用（略）その2

1. ```docker-compose ps``` : Docker内のイメージとか、いまどんな状態？ 何が乗っかっているか、それは動いているのか、など。
2. ```docker-compose ps --service```
3. ```docker-compose exec nginx /bin/bash``` : 中に入った


## いまの内容

動かなくなったぜ！
いちおうRustとnginxとVueを内包しているけど、Rustはもう蚊帳の外って感じ。
nginx上でvueを動かしたかったけどnginxすら動かなくなった。（前は一応Nginxぐらいは動いてた。）

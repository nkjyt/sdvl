# sdvl

## セットアップ
GPUサーバ上で開発を行った．docker-compose.ymlのvolumeを書き換えて，マウントするディレクトリを指定しておくこと．

    $ docker-compose up -d
    $ docker exex -it sdvl_dev /bin/bash
　
コンテナに入ったら，アプリを起動

    $ pip3 install -r requirements.txt
    $ python3 app.py
  研究室のネットワークに接続した状態であれば，ブラウザからgpu〇〇:5000にアクセスすることでアプリを使用できる．

## デプロイ
Flaskによって開発されたアプリは通常1つのリクエストしか処理することができない．そのため，複数人で使用する際にはGunicornなどでWebアプリケーションを並列で実行させる必要がある．今回は，小規模かつ時間の都合上，[Render](https://render.com/)を使ってデプロイ，1人につき1つのアプリを使用してもらった．

## ディレクトリやファイルについて

 - database \
Firebaseからの データの読み込みや受け渡しを行う．
 
 - static \
 画像ファイルや，Firebaseコンフィグなどの静的ファイルを格納．
 
 - templates \
 表示する.htmlファイルを格納．

- app.py \
アプリのルーティングやデータの受け渡しなど，核となるファイル．

## Firebase

Firebaseとの連携に必要な設定ファイルは2つ．公開できないため，以下のディレクトリに保存している．

> //mpshare/impshare/nakajima_yuta/firebase

実行する際は，以下の場所に置く．

    app
    |-static
	|    |-<adminsdk>.json
	|-firebaseConfig.json 

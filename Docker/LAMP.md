[Top](../README.md) > [一覧](../Docker.md)

# LAMP環境構築
LAMP環境構築するのに最初に見たページではこんな感じでやってた
一応うまくいったけどDBとの接続どうやってるか一切説明ないんで勘弁してください→DBコンテナ入れば接続できるかも？

1. プロジェクトフォルダ作成
    ~~~
    mkdir test-project
    ~~~
    <br>

1. サーバ設定データ用フォルダ作成
    ~~~
    mkdir php
    ~~~
    <br>

1. Dockerfile作成
    ~~~
    touch php/Dockerfile
    ~~~
    <br>

1. Dockerfileに下記記述
    ~~~
    FROM php:7.4-apache
    RUN apt-get update && apt-get install -y libonig-dev && \
    docker-php-ext-install pdo_mysql mysqli mbstring
    ~~~
    <br>

1. MySQLデータ用、PHPファイル用フォルダ作成
    ~~~
    mkdir mysql html
    ~~~
    <br>

1. docker-compose.ymlに下記記述
    ~~~
    version: ‘3’

    services:
        mysql:
            image: mysql:5.7
            volumes:
                – ./mysql:/var/lib/mysql
            ports:
                – 3306:3306
            environment:
                – MYSQL_ROOT_PASSWORD=pass
                – MYSQL_DATABASE=db
                – MYSQL_USER=user
                – MYSQL_PASSWORD=dbpass
        php:
            build: ./php
            volumes:
                – ./php.ini:/usr/local/etc/php/php.ini
                – ./html:/var/www/html
            ports:
                – 8080:80
            depends_on:
                – mysql
    ~~~
    <br>

1. コンテナ起動
    ~~~
    docker-compose up -d
    ~~~
    <br>

1. 起動したコンテナ確認
    ~~~
    docker ps
    ~~~
    <br>

1. 適当にHTMLファイル（PHPファイルでも可）作成（ファイル名は「index」にした方がパス指定楽）
1. 「http://localhost:8080」にアクセス
1. ファイルに書いたとおりのWebページが開いてればOK

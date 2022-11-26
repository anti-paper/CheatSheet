[Top](../README.md) > [一覧](../Docker.md)

# DockerCompose
DockerComposeの書き方メモしていく

## 書式
全部じゃないけどネットで見たのはこんな感じ

### 既存イメージ使用
~~~
vresion: バージョン番号
services:
    
    wordpress:
        image: イメージ名
        container_name: コンテナ名
        restart: 再起動設定
        ports:
            - ホスト側ポート番号:コンテナ側ポート番号
        environment:
            環境変数名: 値
    
    mysql:
        image: イメージ名
        conrainer_name: コンテナ名
        restart: 再起動設定
        environment:
            環境変数名: 値
~~~

### Dockerイメージ自作
~~~
vresion: バージョン番号
services:
    
    tomcat:
        build: Dockerfileの存在するディレクトリ
        image: イメージ名
        container_name: コンテナ名
        ports:
            - ホスト側ポート番号:コンテナ側ポート番号
        volumes:
            - ホスト側共有予定ディレクトリ:コンテナ側共有予定ディレクトリ
~~~

## 設定内容
|設定内容|docker runコマンド|docker-compose.yml|
|--|--|--|
|コンテナ名|--name|container_name|
|環境変数|-e|environment|
|ポートフォワード|-p|ports|
|使用するDockerイメージ|コマンドの最後|image|

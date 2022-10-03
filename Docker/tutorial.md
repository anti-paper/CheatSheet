[Top](../README.md) > [一覧](../Docker.md)

# 入門
なんとなくどんなもんか押さえるためのページ<br>
入門って言ってるけど結構内容重たくなってきた<br>
GitBashでエラー出る場合はコマンドプロンプトで試してみ<br>
[参考URL（読めない）](https://docs.docker.com/engine/reference/commandline/docker/)

|コマンド|機能|備考|
|:--:|:--|:--|
|`docker info`|Dockerについての情報確認|-|
|`docker images`|ローカル環境のDockerイメージの一覧確認|-|
|`docker ps -a`|ローカル環境のDockerコンテナの一覧確認|「-a」を省略すると起動中のコンテナのみ表示|
|`docker run image`|「image」という名前のDockerイメージをダウンロード（ダウンロード未了の場合）、コンテナ起動|「-d」付けるとバックグラウンド実行（基本これでいい気がする）<br>「--name」でコンテナ名指定できる<br>「-p hostIP:containerIP」でホスト側IP（外部からアクセスする際のIP）とコンテナ側のIP設定できる<br>「-v hostPath:containerPath」でそれぞれのパスを共有設定|
|`docker pull image`|「image」という名前のDockerイメージをダウンロード|-|
|`docker start container`|「container」という名前のDockerコンテナを起動|-|
|`docker stop container`|「container」という名前のDockerコンテナを停止|-|
|`docker rm container`|「container」という名前（またはID）のDockerコンテナを削除|起動中に削除する場合は「-f」オプション付ける|
|`docker rmi image`|「image」という名前（またはID）のDockerイメージを削除|-|
|`docker exec -it container bash`|「container」という名前のコンテナにログイン|コンテナ内でBash実行できる|
|`docker commit container image`|「container」という名前のコンテナをもとに「image」という名前のイメージを作成|-|
|`docker cp hostFile container:containerDir`|ホスト側の「hostFile」という名前のファイルを「container」という名前のコンテナの「containerDirというディレクトリへコピー」|-|
|`docker cp container:containerFile hostDir`|「container」という名前のコンテナの「containerDirというファイルをホスト側の「hostFile」という名前のディレクトリへコピー」|-|
|`docker build -t image dir`|「dir」にあるDockerfileをもとに「image」という名前のDockerイメージを作成|「-f」オプションで使用するDockerfile指定可能（指定しなければデフォルトで「Dockerfile」が使用される）|
|`docker netowork create netoworkName`|「netoworkName」という名前のDockerネットワークを作成|-|
|`docker netowork ls`|Dockerネットワークを一覧表示|デフォルトで存在する「bridge」はDNS設定なく、名前解決不可のため、新規作成した方が良い|
|`docker network inspect netoworkName`|「netoworkName」という名前のDockerネットワークの詳細情報確認|-|
|`docker run --name mysql --network networkName -e MYSQL_ROOT_PASSWORD=rootpass -d mysql:5.7`|「networkName」という名前のネットワークに接続し、「rootpass」というパスワードでMySQL（5.7）を起動|-|
|`docker run --name workpress --network networkName -e WORDPRESS_DB_PASSWORD=rootpass -p 8080:80 -d wordpress`|「networkName」という名前のネットワークに接続し、「rootpass」というパスワードでwordpressを起動（ホスト側ポートは8080、コンテナ側ポートは80）|WordPressコンテナからアクセスするMySQLポート番号はコンテナ側のもの|
|`docker-compose --version`|Docker Composeのバージョン情報確認|結果的にインストール済みかの確認にもなってる<br>Dockerとは別でインストール必要とのことだけどなんか入れた覚えないのに入ってた……|
|`docker-compose up -d`|Docker Composeを使用してコンテナをバックグラウンド起動|docker-compose.ymlが置かれてるディレクトリで実行する|
|`docker-compose ps`|起動状態の確認|「State」が「Up」になってればOK|
|`docker-compose build`|Dockerイメージのビルド|-|
|`docker-compose stop`|Dockerコンテナの停止|-|
|`docker-compose rm`|Dockerコンテナの削除|「-f」オプション付けると強制削除（yes/no聞かれない）|
|`docker-compose down`|Dockerコンテナの停止、削除、ネットワーク削除|「--rmi all」オプション付けるとイメージも削除|

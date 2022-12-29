[Top](../README.md) > [一覧](../Docker.md)

# 入門
なんとなくどんなもんか押さえるためのページ<br>
入門って言ってるけど結構内容重たくなってきた<br>
GitBashでエラー出る場合はコマンドプロンプトで試してみ<br>

## コマンド一覧
`docker-compose`は`docker compose`でも可（Macの場合はハイフン非対応）

|機能|コマンド|備考|
|--|--|--|
|Dockerについての情報確認|`docker info`|-|
|ローカル環境のDockerイメージの一覧確認|`docker images`|-|
|ローカル環境のDockerイメージの一覧確認（イメージ名のみ）|`docker images -q`|-|
|ローカル環境のDockerコンテナの一覧確認|`docker ps -a`|「-a」を省略すると起動中のコンテナのみ表示|
|ローカル環境のDockerコンテナの一覧確認（コンテナ名のみ）|`docker ps -a -q`|「-a」を省略すると起動中のコンテナのみ表示|
|「image」という名前のDockerイメージをダウンロード（ダウンロード未了の場合）、コンテナ起動|`docker run image`|「-d」付けるとバックグラウンド実行（基本これでいい気がする）<br>「--name」でコンテナ名指定できる<br>「-p hostIP:containerIP」でホスト側IP（外部からアクセスする際のIP）とコンテナ側のIP設定できる<br>「-v hostPath:containerPath」でそれぞれのパスを共有設定|
|「image」という名前のDockerイメージをダウンロード|`docker pull image`|-|
|「container」という名前のDockerコンテナを起動|`docker start container`|-|
|「container」という名前のDockerコンテナを停止|`docker stop container`|-|
|「container」という名前（またはID）のDockerコンテナを削除|`docker rm container`|起動中に削除する場合は「-f」オプション付ける<br>`dokcer ps -a -q`の結果をコンテナ名に指定することで一括削除可能<br>`dokcer rm 'docker ps -a -q'`|
|「image」という名前（またはID）のDockerイメージを削除|`docker rmi image`|`dokcer images -q`の結果をイメージ名に指定することで一括削除可能<br>`dokcer rmi 'docker images -q'`|
|「container」という名前のコンテナにログイン|`docker exec -it container bash`|コンテナ内でBash実行できる|
|「container」という名前のコンテナをもとに「image」という名前のイメージを作成|`docker commit container image`|-|
|ホスト側の「hostFile」という名前のファイルを「container」という名前のコンテナの「containerDirというディレクトリへコピー」|`docker cp hostFile container:containerDir`|-|
|「container」という名前のコンテナの「containerDirというファイルをホスト側の「hostFile」という名前のディレクトリへコピー」|`docker cp container:containerFile hostDir`|-|
|「dir」にあるDockerfileをもとに「image」という名前のDockerイメージを作成|`docker build -t image dir`|「-f」オプションで使用するDockerfile指定可能（指定しなければデフォルトで「Dockerfile」が使用される）|
|「netoworkName」という名前のDockerネットワークを作成|`docker netowork create netoworkName`|-|
|Dockerネットワークを一覧表示|`docker netowork ls`|デフォルトで存在する「bridge」はDNS設定なく、名前解決不可のため、新規作成した方が良い|
|「netoworkName」という名前のDockerネットワークの詳細情報確認|`docker network inspect netoworkName`|-|
|「networkName」という名前のネットワークに接続し、「rootpass」というパスワードでMySQL（5.7）を起動|`docker run --name mysql --network networkName -e MYSQL_ROOT_PASSWORD=rootpass -d mysql:5.7`|-|
|「networkName」という名前のネットワークに接続し、「rootpass」というパスワードでwordpressを起動（ホスト側ポートは8080、コンテナ側ポートは80）|`docker run --name workpress --network networkName -e WORDPRESS_DB_PASSWORD=rootpass -p 8080:80 -d wordpress`|WordPressコンテナからアクセスするMySQLポート番号はコンテナ側のもの|
|Docker Composeのバージョン情報確認|`docker-compose --version`|結果的にインストール済みかの確認にもなってる<br>Dockerインストール時に自動的に入る|
|Docker Composeを使用してコンテナをバックグラウンド起動|`docker-compose up -d`|docker-compose.ymlが置かれてるディレクトリで実行する|
|起動状態の確認|`docker-compose ps`|「State」が「Up」になってれば実行中|
|Dockerイメージのビルド|`docker-compose build`|-|
|Dockerコンテナの停止|`docker-compose stop`|-|
|Dockerコンテナの削除|`docker-compose rm`|「-f」オプション付けると強制削除（yes/no聞かれない）|
|Dockerコンテナの停止、削除、ネットワーク削除|`docker-compose down`|「--rmi all」オプション付けるとイメージも削除|

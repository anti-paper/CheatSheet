[Top](/README.md) > [AWS](/AWS.md)

# Linux2でLAMP環境構築
Linux2を使ってLAMP環境を構築する方法、その他便利な環境構築方法をご紹介


ec2→linux2,新規セキュリティグループ
セキュリティグループ→インバウンドにhttp(80),https(443)追加→ssh(22)削除
IAMロール→「ssmmanaged」検索→アタッチ→インスタンス再起動
Elastic IP→割り当て→関連付け
ソフトウェアアップデート→コマンド「sudo yum update -y」実行
LAMP MariaDB,Amazon Linux 2 PHPパッケージの最新バージョン取得→コマンド「sudo amazon-linux-extras install -y lamp-mariadb10.2-php7.2 php7.2」実行
Amazon Linux のバージョンを表示（パッケージ取得時にエラー発生した場合）→コマンド「cat /etc/system-release」実行
LAMP関連パッケージ,依存関係インストール→コマンド「sudo yum install -y httpd mariadb-server」実行
パッケージバージョン表示→コマンド「yum info パッケージの名前」実行
Apache起動→コマンド「sudo systemctl start httpd」実行
システムブート時自動でApache起動→コマンド「sudo systemctl enable httpd」実行
Apache起動状況確認→コマンド「sudo systemctl is-enabled httpd」実行
ユーザ名取得→コマンド「whoami」実行
ユーザをグループに追加→コマンド「sudo usermod -aG グループ名 ユーザ名」実行（インスタンスに再接続で反映される）
グループのメンバーシップ検証→コマンド「groups」実行
/var/www とそのコンテンツのグループ所有権を変更→コマンド「sudo chown -R ユーザ名:グループ名 /var/www」実行
グループの書き込み許可（ディレクトリ）追加、サブディレクトリにグループ ID 設定→コマンド「sudo chmod 2775 /var/www && find /var/www -type d -exec sudo chmod 2775 {} \;」実行
グループの書き込み許可（ファイル）追加→コマンド「find /var/www -type f -exec sudo chmod 0664 {} \;」実行
Apacheドキュメントルート→/var/www/html/
ローカルタイムの設定→コマンド「sudo ln -sf /usr/share/zoneinfo/Japan /etc/localtime」実行
必要なパッケージがすべてインストールされたことの確認（テスト時にPHPファイル正しく表示されない場合）→コマンド「sudo yum list installed httpd mariadb-server php-mysqlnd」実行
MySQL起動→コマンド「sudo systemctl start mariadb」実行
MySQL設定→コマンド「sudo mysql_secure_installation」実行→最初そのままEnter→次はrootのパスワード変更する場合は「Y」変更しない場合は「n」でEnter
→他は全て「Y」Enter
システムブート時自動でMySQL起動→コマンド「sudo systemctl enable mariadb」実行
MySQL起動状況確認→コマンド「sudo systemctl is-enabled mariadb」実行
phpMyAdmin依存ファイルインストール→コマンド「sudo yum install php-mbstring php-xml -y」実行
Apache再起動→コマンド「sudo systemctl restart httpd」実行
php-fpm再起動→コマンド「sudo systemctl restart php-fpm」実行
Apacheドキュメントルートに移動→コマンド「cd /var/www/html/」実行
最新のphpMyAdminリリース用のソースパッケージをダウンロード→コマンド「wget https://www.phpmyadmin.net/downloads/phpMyAdmin-latest-all-languages.tar.gz」実行
phpMyAdminフォルダの作成及びパッケージの展開→コマンド「mkdir phpMyAdmin && tar -xvzf phpMyAdmin-latest-all-languages.tar.gz -C phpMyAdmin --strip-components 1」実行
展開前パッケージの削除→コマンド「rm phpMyAdmin-latest-all-languages.tar.gz」実行

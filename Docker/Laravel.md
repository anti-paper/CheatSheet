[Top](../README.md) > [一覧](../Docker.md)

# Laravel環境構築
環境構築の情報はここにまとめとく<br>
実際の開発内容は別途まとめる
<br><br>

## 手順
1. プロジェクト作成
   1. sailインストール
      1. `curl -s "https://laravel.build/example-app" | bash`
   1. パスワード求められるため端末のパスワードを入力
1. イメージ構築
   1. プロジェクトディレクトリに移動
      1. `cd example-app`
   1. コンテナ起動
      1. `./vendor/bin/sail up -d`
1. デフォルト画面の表示
   1. localhostにアクセス（デフォルトの80番ポートを使用する場合はポート番号省略可能）
      1. http://localhost:80
1. 使用ポート番号変更（任意）
   1. .envファイルにAPP_PORTを定義 OR ${APP_PORT:-80}のデフォルト値を変更
   1. コンテナ再起動
      1. コンテナ停止
         1. `./vendor/bin/sail down`
      1. コンテナ起動
         1. `./vendor/bin/sail up -d`
1. ./vendor/bin/sailに別名付ける（一般的には「sail」）
   1. ホームディレクトリ直下の~/.bashrcファイルの最後にエイリアス追記
      1. `alias sail './vendor/bin/sail'`
1. phpMyAdminインストール
   1. docker-compose.ymlのserviceブロック内に下記を追記
      ```
      phpmyadmin:
         imgae: phpmyadmin/phpmyadmin
         links:
            - mysql:mysql
         ports:
            - 8080:80
         environment:
            PMA_USER: "${DB_USERNAME}"
            PMA_PASSWORD: "${DB_PASSWORD}"
            PMA_HOST: mysql
         networks:
            - sail
      ```
      portsは:以前がネイティブのポート番号（ブラウザ等でアクセスするポート番号）で、:以降がコンテナ内のポート番号<br>
      PMA_USERとPMA_PASSWORDを上記のように設定することで、phpMyAdminにアクセスした際に自動でログインされる

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
   1. プロジェクトディレクトリ直下の/.bashrcファイル（なければ作成）にエイリアス追記
      1. `alias sail './vendor/bin/sail'`

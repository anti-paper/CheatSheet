[Top](/README.md) > [AWS](/AWS.md)

# Linux2でLaravel環境構築
Linux2を使ってLaravel環境を構築する方法、その他便利な環境構築方法をご紹介


composerインストール→コマンド「curl -sS https://getcomposer.org/installer | php」実行
composerの移動＆名前変更→コマンド「sudo mv composer.phar /usr/local/bin/composer」実行
アプリケーション用ディレクトリ作成→コマンド「composer create-project laravel/laravel dName」実行（dNameはディレクトリ名）
アプリケーション用ディレクトリに移動→コマンド「cd dName」実行
（オプション）データベース操作→コマンド「php artisan tinker」実行
（オプション）artisan tinker終了→コマンド「exit」実行
（オプション）全データ取り出し→コマンド「テーブル名::all()」実行
（オプション）特定idのデータ取り出し→以下コマンド実行
$変数名=テーブル名::find(id)
$変数名->カラム名（特定カラム出力の場合）
$変数名（値そのまま出力の場合）
（オプション）レコード追加→以下コマンド実行
$変数名=new テーブル名()
$変数名->カラム名='データ'（データ入力したいカラム数分実行）
$変数名->save()
（オプション）特定idのデータ取り出し＆削除→以下コマンド実行
$変数名=テーブル名::find(id)
$変数名->delete()
Form用ライブラリのインストール→コマンド「composer require laravelcollective/html」実行
インストール済ライブラリ確認→コマンド「composer info」実行
ユーザ管理機能自動生成→以下コマンド実行
composer require laravel/ui --dev
php artisan ui vue --auth
登録済みルート確認→コマンド「php artisan route:list」実行
カラム追加用ライブラリインストール→コマンド「composer require doctrine/dbal」実行

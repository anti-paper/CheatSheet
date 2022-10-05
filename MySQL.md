# MySQL
MySQLのSQL文メモってくぞ

|SQL文|機能|備考|MySQLモニタ使用|
|:--:|:--|:--|:--|
|`set password for ユーザ名@ホスト名=password('新しいパスワード');`|パスワード変更|-|Yes|
|`mysqladmin password 新しいパスワード -u ユーザ名 -p`|パスワード変更|コマンド実行後現在のパスワード求められる|No|

[Top](../README.md) > [一覧](../Docker.md)

# Dockerfile
Dockerfileの書き方よくわからんからネットで調べた内容メモしとく（一旦まとめたけど結局書き方よくわからん）<br>
<strong style="color:red;">※Dockerfile内でcdしてもDockerfile内のファイルアクセス時には干渉しない（cd使いたい場合は「&&」で繋ぐ）</strong><br>
<br><br>

## 各命令

### FROM
ベースにするDockerイメージを指定<br>
Dockerイメージダウンロード未了の場合自動でダウンロードされる（docker runと同じ？）
<br><br>

### RUN
OSのコマンド実行する際に使用<br>
installの場合途中でインストールするか聞かれると処理止まるので「-y」しておく
<br><br>

### ADD
tar.gzファイルのコンテナへのコピーと、tarの展開を行う<br>
「ADD <コピー元> <Dockerイメージ内のコピー・展開先>」の書き方
<br><br>

### COPY
ADDからtar展開処理を除いたもの（コピーのみ行う）
<br><br>

### CMD
コンテナ起動時に実行するコマンドを記述
<br><br>

### USER
`USER ユーザ名[:ユーザグループ名]`<br>
OR<br>
`USER ユーザID[:ユーザグループID]`<br>
でアクティブユーザを設定できる<br>
グループ指定する場合、ユーザは指定したグループに「のみ」所属する<br>
（他のグループ所属の設定は無視される）
<br><br>

### WORKDIR
Dockerfile内でコマンド実行する際の作業ディレクトリを指定<br>
存在しないディレクトリを指定すると新規作成される（エラーにはならない）
<br><br>

## ワンポイントアドバイス的なもの
命令とは違う話だけどなんか役に立ちそうな話

### キャッシュ
Dockerfileで実行済みのコマンドはキャッシュされる<br>
変更されない限りはキャッシュが使用される（出力結果に「★印が付く」）<br>
変更箇所が最初に登場してからは後で変更ない箇所があってもキャッシュは使用されない<br>
→ほぼOR全く変更ない処理（インストール等）は先に書く方が効率良い（ビルドの時間短縮できる）<br>

### 実行単位
各コマンドごとにレイヤー作成される<br>
→Dockerイメージでかくなる<br>
→作成できるレイヤー数に上限（128）もある<br>
→なるべくまとめる<br>
→キャッシュとも相談しながらまとめられる単位を策定する

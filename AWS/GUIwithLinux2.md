[Top](/README.md) > [AWS](/AWS.md)

# Linux2でGUI実装
Linux2を使ってGUIを実装する方法、その他便利な環境構築方法をご紹介

|やりたいこと|手順|備考|
|--|--|--|
|接続時に指定するポート番号許可|1. セキュリティグループ<br>2. カスタムTCPルール<br>3. 5901|安全のためマイパブリックIPのみ許可が望ましい|
|MATEデスクトップのインストール|`sudo amazon-linux-extras install -y mate-desktop1.x`|-|
|全ユーザに対し、MATEをデフォルトのデスクトップとして定義|`sudo bash -c 'echo PREFERRED=/usr/bin/mate-session>/etc/sysconfig/desktop'`|-|
|TigerVNCパッケージのインストール|`sudo yum install -y tigervnc-server`|-|
|VNCパスワード設定|1. `vncpasswd`<br>設定するパスワード入力（確認込みで2回）<br>閲覧用パスワード設定（yかnで回答）|-|
|VNCサーバ用の新規sstemdユニット作成|`sudo cp /lib/systemd/system/vncserver\@.service /etc/systemd/system/vncserver\@.service`|-|
|VNCサーバ用ユニットの全「<USER>」文字列をssm-userに置き換え|`sudo sed -i 's/<USER>/ssm-user/' /etc/systemd/system/vncserver\@.service`|-|
|systemdマネージャ設定の再読み込み|`sudo systemctl daemon-reload`|-|
|サービス有効化|`sudo systemctl enable vncserver@:1`|-|
|サービス起動|`sudo systemctl start vncserver@:1`|-|


-------------------------------------ここからWin特有操作----------------------------------------------<br>
「TigerVNC」検索→サイトにアクセス
→「GitHub release page.」リンク
→ダウンロードリンク（「vncviewerビット数-バージョン番号.exe」）
vncviewer起動→「EC2パブリックIP（DNS）:セキュリティグループで許可したポート番号」でConnect
→vncpasswdで設定したパスワード入力


日本語入力機能インストール→コマンド「sudo yum install -y ibus-kkc」実行
日本語フォントのインストール→コマンド「sudo yum install -y google-noto-sans-japanese-fonts」実行
環境変数設定→コマンド「vim ~/.bashrc」実行→下記追記
--------------------------------------------------
export GTK_IM_MODULE=ibus
export XMODIFIERS=@im=ibus
export QT_IM_MODULE=ibus
ibus-daemon -drx
--------------------------------------------------

ロケールの設定→以下コマンド実行
--------------------------------------------------
sudo localectl set-locale LANG=ja_JP.UTF-8
sudo localectl set-keymap jp106
sudo localectl set-keymap jp-OADG109A
--------------------------------------------------

再起動→コマンド「sudo reboot now」実行


レポジトリ作成→コマンド「sudo vim /etc/yum.repos.d/google-chrome.repo」実行
→以下の内容を記述し、「ZZ」で上書き保存
--------------------------------------------------------------
[google-chrome]
name=google-chrome
baseurl=http://dl.google.com/linux/chrome/rpm/stable/$basearch
enabled=0
gpgcheck=1
gpgkey=https://dl-ssl.google.com/linux/linux_signing_key.pub
--------------------------------------------------------------
Google Chromeインストール→コマンド「sudo yum install -y --enablerepo=google-chrome google-chrome-stable」実行

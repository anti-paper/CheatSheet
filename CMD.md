[Top](README.md)

# コマンドプロンプト
必要になったコマンドを片っ端からメモる
<br><br>

## 一覧

|機能|コマンド|備考|
|--|--|--|
|コマンドプロンプトの終了|exit|-|
|コマンドの履歴の表示|↑|F7で一覧表示|
|テキストファイルの内容の表示|type ファイルパス|linuxコマンドのcatに相当<br>新規ファイル作成時は「type nul > ファイル名」|
|出力先の変更（リダイレクト）|コマンド>ファイル名|指定したファイルにコマンドの実行結果が出力される<br>追記の場合は「>」を「>>」に変更して実行|
|MASM32のプログラムソースファイルをアセンブルする|\masm32\bin\ml /c /coff プログラムソースファイル名|「\masm32\bin\」はml.exeがあるフォルダ名<br>オプション/cはアセンブルだけしてリンクしないことを指示する<br>/coffはCOFFフォーマットという形式のオブジェクトファイルを生成することを意味する<br>プログラムソースファイルは拡張子が「.asm」のもの|
|MASM32のオブジェクトファイルをリンクする|\masm32\bin\link /subsystem:console オブジェクトファイル名|「\masm32\bin\」はml.exeがあるフォルダ名<br>/subsystem:consoleはコンソールアプリケーション（ウィンドウを使わないアプリケーション）としてリンクすることを意味する<br>オブジェクトファイルは拡張子が「.obj」のもの|
<br><br>

[その他コマンドはこちら](https://www.javadrive.jp/command/)
<br><br>

## 公式ドキュメント
[Windows のコマンド](https://learn.microsoft.com/ja-jp/windows-server/administration/windows-commands/windows-commands)

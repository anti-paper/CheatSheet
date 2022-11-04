[Top](../../README.md) > [Visual Studio Codeメモ](../../VSCode.md) > [機能](../func.md)

# デバッグ設定
## 設定ファイル情報

|パス|ファイル名|
|--|--|
|.vscode/|launch.json|
<br><br>

## 設定ファイル作成
デバッグビュー設定のボタンをはじめて押下した際自動生成される
<br><br>

## 設定項目
|項目名|内容|
|--|--|
|name|設定の名称<br>デバッグビュー中のドロップダウンリストに、起動するデバッグ設定の名前として表示される|
|type|デバッグする言語、環境の種類<br>使う拡張機能が指定する名称を記述|
|request|デバッグ開始時にプロセスを起動する「launch」か、起動中のプロセスにデバッガーを接続する「attach」のいずれかを選択<br>拡張機能のREADME要確認|
|program|実行するプログラム<br>pythonの場合は「python」ではなく「script.py」（実行プログラム）|
|args|プログラム実行時に指定する引数|
|cwd|プログラム実行時の作業フォルダ|
|env|環境変数<br>nullを指定すると削除される|
|windows<br>osx<br>linux|OSごとの設定<br>既存の設定を上書きする<br>「args」に限り、既存の設定の後ろに追加|
|useWSL|Windows且つWindows System for Linux上で実行する場合はtrue|
|console|デバッグをどのコンソール上で起動するか<br>・internalConsole：パネルのデバッグコンソールタブで実行される（デフォルト値）<br>・integratedTerminal：パネルのターミナルタブのターミナルで実行される<br>externalTerminal：外部ターミナルで実行される<br>　実行するターミナルは設定ファイル（settings.json）の<br>　「terminal.external.osxExec」、<br>　「terminal.external.windowsExec」、<br>　「terminal.external.linuxExec」で設定可能|
|internalConsoleOption|デバッグ開始時にパネルをデバッグコンソールタブに切り替えるかどうか|
|preLaunchTask|デバッグ実行の前に実行するタスク<br>ビルドのタスクなどを指定|
|postDebugTask|デバッグ実行の終了時に実行するタスク|
<br><br>

## 変数
|変数名|内容|カテゴリ|
|--|--|--|
|${workspaceFolder}|フルパス|ワークスペースのフォルダに関する変数|
|${workspaceFolderBasename}|ディレクトリ名|ワークスペースのフォルダに関する変数|
|${file}|フルパス|現在エディタで開いているファイルに関する変数|
|${relativeFile}|ワークスペースからのパス|現在エディタで開いているファイルに関する変数|
|${fileBasename}|ファイル名|現在エディタで開いているファイルに関する変数|
|${fileBasenameNoExtension}|ファイル名から拡張子を除いたもの|現在エディタで開いているファイルに関する変数|
|${fileDirname}|ディレクトリ名|現在エディタで開いているファイルに関する変数|
|${fileExtname}|拡張子|現在エディタで開いているファイルに関する変数|
|${cwd}|事前実行のタスクの起動したディレクトリ|その他の変数|
|${lineNumber}|デバッグを実行した行番号|その他の変数|
|${env.NAME}|任意の環境変数（NAMEは必ず全て大文字とする必要がある）|その他の変数|
|${config:Name}|settings.json内の「Name」の設定値|その他の変数|
<br><br>

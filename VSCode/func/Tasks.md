[Top](../../README.md) > [Visual Studio Codeメモ](../../VSCode.md) > [機能](../func.md)

# タスク設定
## 設定ファイル情報

|パス|ファイル名|
|--|--|
|.vscode/|tasks.json|
<br><br>

## 設定ファイル作成
コマンド「タスク：タスクの構成（Tasks: Configure Task）」を実行<br>
自動認識されたタスクを選択した際自動的にtasks.jsonに追記される
<br><br>

## 設定項目
|項目名|内容|
|--|--|
|type|実行方法の種類（必須）<br>「shell」「process」の場合は、「command」「args」使用でコマンド実行される<br>通常は「shell」を使用する|
|label|タスクの名称|
|command|実行コマンド|
|args|コマンドに渡される引数のリスト|
|option|タスク実行時の環境を指定するオプション項目<br>シェルでコマンド実行する際の環境をJSONオブジェクトで指定<br>使用可能項目は以下の通り<br>・shell：コマンド実行するシェル<br>・env：環境変数<br>・cwd：実行時のカレントフォルダ<br>「shell」指定しなかった場合、bash（macOS,Linux）又はPowershell（Windows）が使用される|
|osx<br>windows<br>linux|OSごとのcommand、args、optionを個別に設定する際に使う|
|runOption|実行時の詳細設定<br>JSONオブジェクトで指定<br>使える項目は以下の通り<br>・reevaluateOnReturn：タスクの再実行時、${file}等の変数を再評価するかどうか。デフォルト値はtrue<br>・runOn：「folderOpen」を設定した場合、ワークスペースを開いた時点で自動で実行される。指定しない場合又は「default」を設定した場合は手動で実行する必要あり|
|problemMatcher|タスクの出力と問題マッチャーとの対応の設定|
|group|タスクの一覧を表示する際のグループ<br>デフォルト値は「none」<br>「build」「test」の2種類|
|dependsOn|依存するタスク、すなわち事前に実行すべきタスクを列挙|
|isBackground|問題マッチャーをバックグラウンドで実行させ続けるかどうか<br>デフォルト値はfalse|
|promptOnClose|タスクの実行中にVSCodeを閉じるときにユーザにダイアログを表示するかどうか<br>デフォルト値はfalse|
|presentation|タスクの表示に関する設定<br>JSON形式で指定<br>使える項目は以下の通り<br>・echo：実行したコマンドをターミナルに表示するかどうか。デフォルト値はtrue<br>・reveal：タスク実行時にターミナルを表示するか。以下の値から指定<br>　・always：タスクを開始したときに表示<br>　・silent：エラーになったときのみ表示<br>　・never：エラーになってもターミナルタブを表示しない<br>・focus：実行時にパネルのターミナルタブを開くかどうか。デフォルト値はfalse<br>・panel：タスク間でパネルのターミナルタブ内のターミナルを共有するか。以下の値から指定。デフォルト値はshared<br>　・shared：複数のタスクでターミナルを共有<br>　・dedicated：同一のタスクの再実行のときにはターミナルを共有<br>　・new：タスクを実行するたびにターミナルを開始|
<br><br>

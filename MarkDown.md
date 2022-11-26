[Top](README.md)

# MarkDown
記法メモしていく<br>
※「\」でエスケープする<br>
[参考URL](https://qiita.com/tbpgr/items/989c6badefff69377da7)

## 一覧

|機能|記述|備考|
|--|--|--|
|「test」という文字列をH1相当の見出しにする|`# test`|「#」の数によって6段階の見出しが作れる|
|「test」という文字列を箇条書きにする|`- test`|「-」と項目名の間に半角スペース必要<br>インデントは半角スペース2～5個で1段階<br>最大で3段階<br>4段階目以降は3段階目と同じ記号が付される|
|「test」という文字列を番号付きリストにする|`1. test`|「1.」と項目名の間に半角スペース必要<br>インデントは半角スペース3～6個で1段階|
|タブOR半角スペース4つでコードブロックをpre表示可能|`    def test():`<br>`        return 'test'`|インデントの度にタブOR半角スペース4つ<br>コードブロックから抜け出すにはインデントをクリアする必要あり|
|「`` ` ``」で囲った文字列がコードとして認識される|`` ` ``pwd`` ` ``|文字列として「`` ` ``」を表示させる場合は、表示させたい数以上の「`` ` ``」で囲う必要あり|
|斜体（\<em>強調）|`*test*`<br>OR<br>`_test_`|-|
|太字（\<strong>強調）|`**test**`<br>OR<br>`__test__`|-|
|斜体太字（\<em> + \<strong>強調）|`***test***`<br>OR<br>`___test___`|-|
|水平線|`***`<br>OR<br>`___`<br>`---`|間に空白があってもよい|
|「test」という文字列に「test.txt」へのリンクを設定する|`[test](test.txt)`|リンクはローカルファイルへのリンクでもWeb上のリンクでも可|
|「ref」という文字列に、「def」として定義したリンクを設定する|`[def]: test.txt`<br>`[ref][def]`|定義と参照は前後逆転しても問題なし<br>定義と参照は最低1行以上開ける必要あり|
|「test」という文字列に取り消し線を設定する|`~~test~~`|GFM（Github Flavored Markdown）特有の記法<br>要はGithubでしか使えない|
|コードブロックをpre表示可能|`~~~`<br>`def test():`<br>`    return 'test'`<br>`~~~`|インデントの度にタブOR半角スペース4つ<br>GFM（Github Flavored Markdown）特有の記法<br>要はGithubでしか使えない|
|コードブロックをpre表示可能|```` ``` ````<br>`def test():`<br>`    return 'test'`<br>```` ``` ````|インデントの度にタブOR半角スペース4つ<br>GFM（Github Flavored Markdown）特有の記法<br>要はGithubでしか使えない|
|「language」で指定した言語のシンタックスハイライトと共にコードブロックをpre表示可能|`~~~language`<br>`def test():`<br>`    return 'test'`<br>`~~~`|インデントの度にタブOR半角スペース4つ<br>GFM（Github Flavored Markdown）特有の記法<br>要はGithubでしか使えない|
|「language」で指定した言語のシンタックスハイライトと共にコードブロックをpre表示可能|```` ```language ````<br>`def test():`<br>`    return 'test'`<br>```` ``` ````|インデントの度にタブOR半角スペース4つ<br>GFM（Github Flavored Markdown）特有の記法<br>要はGithubでしか使えない|
|表組み|`\|header1\|header2\|header3\|`<br>`\|:--\|--:\|:--:\|`<br>`\|左寄せ\|右寄せ\|中央寄せ\|`|コード内のデータに記したように文字列を寄せることができる<br>GFM（Github Flavored Markdown）特有の記法<br>要はGithubでしか使えない|
|「test」という文字列に「header」という見出しへのリンクを設定する|`[test](#header)`|見出しは大文字小文字区別しない（リンク設定時はすべて小文字にする必要あり）<br>スペースやアンダースコア等リンク設定時に指定できない文字あり（Ctrl + Spaceで呼び出せば間違いないので特に気にする必要なし）<br>見出しの深さに関係なくリンク設定時は「#」を1つだけ指定<br>GFM（Github Flavored Markdown）特有の記法<br>要はGithubでしか使えない|
|重複する見出しへのリンクを設定する場合は、2回目以降に登場する見出しについては「-」（半角）の後に半角の数字を指定|`[test](#header-1)`|2回目の場合を1として、1ずつ増やしていく<br>1回目の場合は数字指定なしでそのまま項目名指定<br>GFM（Github Flavored Markdown）特有の記法<br>要はGithubでしか使えない|

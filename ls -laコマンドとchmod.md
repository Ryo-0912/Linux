以下のコマンドを実行すると、隠しファイルも含めて詳細情報を表示することができる。

```php
ls -la
```

実行結果例

```php
-rw-r--r--   1 test-user  staff    1316 10 26 19:30 .env
-rw-r--r--   1 test-user  staff     899 10 21 16:54 .env.example
drwxr-xr-x  15 test-user  staff     480 11  2 20:32 .git
-rw-r--r--   1 test-user  staff      20 10 21 16:54 README.md
drwxr-xr-x  14 test-user  staff     448 10 26 18:59 app
-rw-r--r--   1 test-user  staff    1686 10 21 16:54 artisan
drwxr-xr-x   4 test-user  staff     128 10 21 16:54 bootstrap
-rw-r--r--   1 test-user  staff    1817 11  1 13:25 composer.json
-rw-r--r--   1 test-user  staff  297802 11  1 18:20 composer.lock
```

この実行結果からわかること(左から)

```php
-rw-r--r-- 
```

これは、一番右にあるファイル(今回なら、.envファイル)への権限について書かれている。

●最初の-は、.envがファイル区分であることを表示。

●次の３つ(rw-)は所有者(今回なら、test-user)が対象のファイルにできる権限を記述。
(今回なら、r : 読み取り, w : 書き込みが可能)

●次の３つ(r--)は所有者(今回なら、staff)が対象のファイルにできる権限を記述。
(今回なら、r : 読み取り のみ可能)

●最後の３つ(r--)はその他の全ユーザー(今回なら、staff)が対象のファイルにできる権限を記述。
(今回なら、r : 読み取り のみ可能)


参照1 : https://www.sejuku.net/blog/50161

参照2 : https://qiita.com/shisama/items/5f4c4fa768642aad9e06

ls -laコマンドで表示される各ファイルへのアクセス権限を変更したい時に使うコマンドが「chomd」。

「chmod」コマンドはLinuxでファイルのパーミッションを設定するときに使用するコマンド。

パーミッションとは実行権限のことで、ファイルによって「所有者」「グループ」「その他のユーザ」のそれぞれ権限が割り振られている。

3文字ずつで「所有者」、「グループ」、「その他のユーザー」に対応している

ex) rwxr-xr-x ⇒ (所有者権限)rwx/(グループ権限)r-x/(その他のユーザー権限)r-x

【使用例】所有者やグループによってファイルやプログラムのアクセス権限を指定したい場合に、「chmod」コマンドを使用することで、それぞれの権限を細かく指定することが可能になる。

文字に対応した数値の足し算で数字が変わる

⇒  —- : 0 , —x : 1 , -w- : 2 , -wx : 3 , r— : 4 , r-x : 5 , rw- : 6 , rwx : 7

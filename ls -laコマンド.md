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

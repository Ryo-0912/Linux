```chownコマンド```でファイルやディレクトリの所有者を変更できる。

***形式***
```
chown [オプション] ユーザーorグループ ファイルorディレクトリ
```

**例**

**現在の状況確認**
```
$ ls -l
#=> -rw-rw-r— 1 sample sample 47 5月 21 08:42 test1.htmle.erb
```

**ユーザ所有権変更**
```
$ chown root test1.htmle.erb

$ ls -l
#=> -rw-rw-r— 1 root sample 47 5月 21 08:42 test1.htmle.erb
```

**ユーザ・グループ所有権変更**
```
$ chown root:root test1.htmle.erb

$ ls -l
#=> -rw-rw-r— 1 root root 47 5月 21 08:42 test1.htmle.erb
```

オプション```-R```について

オプションの指定がなければ、ディレクトリ内部の所有者は変更せず、カレントディレクトリのみが対象となる。

```-R```オプションを指定することで、カレントディレクトリ配下のファイルやディレクトリの所有者を変更できる。

例
```
sample % ls -la ./config
total 192
drwxr-xr-x  21 andouryou  staff    672  2 26 16:43 .
drwxr-xr-x  42 andouryou  staff   1344  3 27 13:26 ..
-rw-r--r--   1 andouryou  staff  10452 12 21 13:53 app.php
-rw-r--r--   1 andouryou  staff   3993  8 23  2023 auth.php
-rw-r--r--   1 andouryou  staff   1860  6 15  2023 broadcasting.php
-rw-r--r--   1 andouryou  staff   3274  6 15  2023 cache.php
-rw-r--r--   1 andouryou  staff   1599  6 15  2023 cors.php
-rw-r--r--   1 andouryou  staff   5291  6 15  2023 database.php
-rw-r--r--   1 andouryou  staff   2372  6 15  2023 filesystems.php
drwxr-xr-x   3 andouryou  staff     96  6 15  2023 firebase
-rw-r--r--   1 andouryou  staff   7881  6 15  2023 firebase.php
-rw-r--r--   1 andouryou  staff   1573  6 15  2023 hashing.php
-rw-r--r--   1 andouryou  staff    514  6 15  2023 image.php
drwxr-xr-x   4 andouryou  staff    128  6 15  2023 jwt
-rw-r--r--   1 andouryou  staff  10042  6 15  2023 jwt.php
-rw-r--r--   1 andouryou  staff   3755  6 15  2023 logging.php
-rw-r--r--   1 andouryou  staff   3600  6 15  2023 mail.php
-rw-r--r--   1 andouryou  staff   2906  6 15  2023 queue.php
-rw-r--r--   1 andouryou  staff   3326  2 26 16:43 services.php
-rw-r--r--   1 andouryou  staff   7025  6 15  2023 session.php
-rw-r--r--   1 andouryou  staff   1053  6 15  2023 view.php

sample % sudo chown -R root ./config
Password:

sample % ls -la ./config            
total 192
drwxr-xr-x  21 root       staff    672  2 26 16:43 .
drwxr-xr-x  42 andouryou  staff   1344  3 27 13:26 ..
-rw-r--r--   1 root       staff  10452 12 21 13:53 app.php
-rw-r--r--   1 root       staff   3993  8 23  2023 auth.php
-rw-r--r--   1 root       staff   1860  6 15  2023 broadcasting.php
-rw-r--r--   1 root       staff   3274  6 15  2023 cache.php
-rw-r--r--   1 root       staff   1599  6 15  2023 cors.php
-rw-r--r--   1 root       staff   5291  6 15  2023 database.php
-rw-r--r--   1 root       staff   2372  6 15  2023 filesystems.php
drwxr-xr-x   3 root       staff     96  6 15  2023 firebase
-rw-r--r--   1 root       staff   7881  6 15  2023 firebase.php
-rw-r--r--   1 root       staff   1573  6 15  2023 hashing.php
-rw-r--r--   1 root       staff    514  6 15  2023 image.php
drwxr-xr-x   4 root       staff    128  6 15  2023 jwt
-rw-r--r--   1 root       staff  10042  6 15  2023 jwt.php
-rw-r--r--   1 root       staff   3755  6 15  2023 logging.php
-rw-r--r--   1 root       staff   3600  6 15  2023 mail.php
-rw-r--r--   1 root       staff   2906  6 15  2023 queue.php
-rw-r--r--   1 root       staff   3326  2 26 16:43 services.php
-rw-r--r--   1 root       staff   7025  6 15  2023 session.php
-rw-r--r--   1 root       staff   1053  6 15  2023 view.php
```

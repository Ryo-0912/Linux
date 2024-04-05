

参照 : https://uxmilk.jp/52356

```
sudo su (ユーザ名)
```
suコマンドに引数なし ⇒ rootユーザとしてユーザ切り替える

suコマンドに引数(ユーザ名)あり ⇒ 引数で指定したユーザに切り替える

# sudo権限あるか確認

```
[sample-XXX@ip-YY-YY-YY-YYY ~]$ sudo -l
既定値のエントリと照合中 (ユーザー名 sample-XXX) (ホスト名 ip-YY-YY-YY-YYY):
    !visiblepw, always_set_home, match_group_by_gid, always_query_group_plugin, env_reset, env_keep="COLORS DISPLAY HOSTNAME HISTSIZE KDEDIR LS_COLORS", env_keep+="MAIL PS1 PS2 QTDIR USERNAME LANG
    LC_ADDRESS LC_CTYPE", env_keep+="LC_COLLATE LC_IDENTIFICATION LC_MEASUREMENT LC_MESSAGES", env_keep+="LC_MONETARY LC_NAME LC_NUMERIC LC_PAPER LC_TELEPHONE", env_keep+="LC_TIME LC_ALL LANGUAGE LINGUAS
    _XKB_CHARSET XAUTHORITY", secure_path=/sbin\:/bin\:/usr/sbin\:/usr/bin

ユーザー skrum-ando は ip-YY-YY-YY-YYY 上で コマンドを実行できます
    (ALL) ALL
    (ALL) NOPASSWD: ALL
```

# サーバに作成されているユーザ一覧取得

```
cat /etc/passwd 　※passwordではない
```


# 特定のユーザにsudo権限があるか確認

```
[root@ip-YY-YY-YY-YYY sample-AAA]#　id sample-AAA
uid=1010(sample-AAA) gid=1010(sample-AAA) groups=1010(sample-AAA),10(wheel)
```

この結果から、わかること。

ユーザid : 1010
プライマリグループID : 1010
wheelグループ所属 => ***sample-AAAはsudo権限を持っている****


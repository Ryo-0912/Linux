# ユーザの切り替え

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

- ユーザid : 1010
- プライマリグループID : 1010
- wheelグループ所属 => ***sample-AAAはsudo権限を持っている****

# sudoの設定ファイル

```
[root@ip-YY-YY-YY-YYY sample-XXX]# sudo visudo

# this option is only effective for configurations where either
# env_reset is disabled or HOME is present in the env_keep list.
#
Defaults    always_set_home
Defaults    match_group_by_gid

# Prior to version 1.8.15, groups listed in sudoers that were not
# found in the system group database were passed to the group
# plugin, if any. Starting with 1.8.15, only groups of the form
# %:group are resolved via the group plugin by default.
# We enable always_query_group_plugin to restore old behavior.
# Disable this option for new behavior.
Defaults    always_query_group_plugin

Defaults    env_reset
Defaults    env_keep =  "COLORS DISPLAY HOSTNAME HISTSIZE KDEDIR LS_COLORS"
Defaults    env_keep += "MAIL PS1 PS2 QTDIR USERNAME LANG LC_ADDRESS LC_CTYPE"
Defaults    env_keep += "LC_COLLATE LC_IDENTIFICATION LC_MEASUREMENT LC_MESSAGES"
Defaults    env_keep += "LC_MONETARY LC_NAME LC_NUMERIC LC_PAPER LC_TELEPHONE"
Defaults    env_keep += "LC_TIME LC_ALL LANGUAGE LINGUAS _XKB_CHARSET XAUTHORITY"

#
# Adding HOME to env_keep may enable a user to run unrestricted
# commands via sudo.
#
# Defaults   env_keep += "HOME"

Defaults    secure_path = /sbin:/bin:/usr/sbin:/usr/bin

## Next comes the main part: which users can run what software on 
## which machines (the sudoers file can be shared between multiple
## systems).
## Syntax:
##
##      user    MACHINE=COMMANDS
##
## The COMMANDS section may have other options added to it.
##
## Allow root to run any commands anywhere 
root    ALL=(ALL)       ALL

## Allows members of the 'sys' group to run networking, software, 
## service management apps and more.
# %sys ALL = NETWORKING, SOFTWARE, SERVICES, STORAGE, DELEGATING, PROCESSES, LOCATE, DRIVERS

## Allows people in group wheel to run all commands
%wheel  ALL=(ALL)       ALL

## Same thing without a password
 %wheel ALL=(ALL)       NOPASSWD: ALL

## Allows members of the users group to mount and unmount the 
## cdrom as root
# %users  ALL=/sbin/mount /mnt/cdrom, /sbin/umount /mnt/cdrom

## Allows members of the users group to shutdown this system
# %users  localhost=/sbin/shutdown -h now

## Read drop-in files from /etc/sudoers.d (the # here does not mean a comment)
#includedir /etc/sudoers.d
```

このファイルは、sudo権限を付与する際にパスワードを設定するかどうかなどの設定を行える。

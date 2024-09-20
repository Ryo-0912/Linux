# grepコマンド

```jsx
grep [オプション] 検索文字列　検索対象ファイル
```

例

```jsx
skrum.development@skrum-staging:/usr/share/nginx/html/current$ grep "22314" storage/logs/laravel-2024-03-15.log

以下、実行結果
[2024-03-15 10:20:03] staging.ERROR: Trying to access array offset on value of type null {"userId":**22314**,"exception":"[object] (ErrorException(code: 0): Trying to access array offset on value of type null at /usr/share/nginx/html/releases/35/app/Services/UserPickupService.php:77)
[2024-03-15 10:20:39] staging.ERROR: Trying to access array offset on value of type null {"userId":**22314**,"exception":"[object] (ErrorException(code: 0): Trying to access array offset on value of type null at /usr/share/nginx/html/releases/35/app/Services/UserPickupService.php:77)
[2024-03-15 10:23:44] staging.ERROR: Trying to access array offset on value of type null {"userId":**22314**,"exception":"[object] (ErrorException(code: 0): Trying to access array offset on value of type null at /usr/share/nginx/html/releases/35/app/Services/UserPickupService.php:77)
[2024-03-15 10:25:31] staging.ERROR: Trying to access array offset on value of type null {"userId":**22314**,"exception":"[object] (ErrorException(code: 0): Trying to access array offset on value of type null at /usr/share/nginx/html/releases/35/app/Services/UserPickupService.php:77)
[2024-03-15 10:27:24] staging.ERROR: Trying to access array offset on value of type null {"userId":**22314**,"exception":"[object] (ErrorException(code: 0): Trying to access array offset on value of type null at /usr/share/nginx/html/releases/35/app/Services/UserPickupService.php:77)
[2024-03-15 10:28:01] staging.ERROR:  {"userId":**22314**,"exception":"[object] (App\\Exceptions\\NoDataException(code: ):  at /usr/share/nginx/html/releases/35/app/Http/UseCases/UserMatchingUseCase.php:31)
p
```


例2
```
grep "200" /var/log/error.log >> /data/work/get_log_file/log_output.txt
```

解説
このコマンドは、「200」という文字列を含むすべての行を、 ```/var/log/error.log ```ファイル内からから探す。

そして、その検索結果を ```/data/work/get_log_file/log_output.txt``` ファイルに追記する。

# >>　と　>

- > : 上書き 既存内容はすべて消去した上で記載。

  例
  
  ```echo "新しいデータ" > ファイル.txt```
   
- >> : 追記　既存内容はそのままで、その後から記載。

  例
  
  ```echo "追記データ" >> ファイル.txt```

- < : 1行の入力を行える

例
  ```sort < ファイル.txt```
  
- << : 複数行の入力を行える。

  例
  
  ```
  cat << END
  これは最初の行です。
  これは次の行です。
  END
  ```

### オプション

| オプション | 説明 |
| ----- | --- |
| -E | http://d.hatena.ne.jp/keyword/%B3%C8%C4%A5%C0%B5%B5%AC%C9%BD%B8%BD(ERE)を利用する※このオプションなしでもhttp://d.hatena.ne.jp/keyword/%C0%B5%B5%AC%C9%BD%B8%BDの「. * ^ $ [ ]」は利用可能 |
| -e [検索文字列] | オプションの引数として検索文字列を指定するこのオプションを複数回使用することでOR検索が可能 |
| -v | 結果を反転する。検索文字列を含む行以外を表示 |
| -i | 検索文字列の大文字と小文字を区別しない |
| -c | マッチした行ではなく、マッチした行数を表示 |
| -m [数字] | [数字]行分だけ表示する |
| -B [数字] | マッチした行の前 [数字] 行を表示 |
| -A [数字] | マッチした行の後 [数字] 行を表示 |
| -C [数字] | マッチした行の前後 [数字] 行を表示 |
| -h | 出力する行の前にファイル名を付けないようにする |
| -n | 頭にそのファイル内での行数を表示 |


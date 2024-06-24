# SQLite3Result::fetchArray

```php
public SQLite3Result::fetchArray(int $mode = SQLITE3_BOTH): array|false
```

結果セットの行を, 連想配列あるいは (通常の) 配列, あるいはその両方で取得する.

## mode

次の行をどのように返すかを制御する. `mode` は以下の通り.

|`mode`|説明|
|---|---|
|`SQLITE3_ASSOC`|連想配列で返す|
|`SQLITE3_NUM`|(通常の) 配列で返す|
|`SQLITE3_BOTH`|連想配列と (通常の) 配列の両方で返す|

なお, `mode` のデフォルトは `SQLITE3_BOTH` .

## 参考文献

- PHP, "SQLite3Result::fetchArray", [https://www.php.net/manual/ja/sqlite3result.fetcharray.php](https://www.php.net/manual/ja/sqlite3result.fetcharray.php), (2024-06-25 参照).
  
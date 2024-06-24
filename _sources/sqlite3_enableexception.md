# SQLite3::enableExceptions

```php
public SQLite3::enableExceptions(bool $enable = false): bool
```

例外のスローを有効にする.

## enable

`true` の場合, SQLite3 のインスタンスと SQLite3Stmt 及び SQlite3Result から派生したインスタンスは, エラー時にスローされる.  
`false` の場合, SQLite3 のインスタンスと SQLite3Stmt 及び SQlite3Result から派生したインスタンスは, エラー時に警告を発生させる.

## 例

```php
<?php
$sqlite = new SQLite3('mydatabase.db');
try {
    $sqlite->enableExceptions(true);
    $sqlite->exec('create table foo');
    $sqlite->exec('create table bar');
} catch (Exception $e) {
    echo 'Caught exception: ' . $e->getMessage();
}
?>
```

**出力：**  

```php
Warning: SQLite3::exec(): near "foo": syntax error in example.php on line 4
Caught exception: near "bar": syntax error
```

## 参考文献

- PHP, "SQLite3::enableExceptions", [https://www.php.net/manual/ja/sqlite3.enableexceptions.php](https://www.php.net/manual/ja/sqlite3.enableexceptions.php), (2024-06-25 参照).
  
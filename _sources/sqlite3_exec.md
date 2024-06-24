# SQLite3::exec

```php
public SQLite3::exec(string $query): bool
```

指定したデータベースに, 結果を返さないクエリを実行する.

## query

実行したい SQL クエリ.

## 例

```php
<?php
$sqlite = new SQLite3('mydatabase.db');

$sqlite->exec('CREATE TABLE mytable (word TEXT)');
?>
```

## 参考文献

- PHP, "SQLite3::exec", [https://www.php.net/manual/ja/sqlite3.exec.php](https://www.php.net/manual/ja/sqlite3.exec.php), (2024-06-25 参照).
  
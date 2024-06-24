# SQLite3Stmt::execute

```php
public SQLite3Stmt::execute(): SQLite3Result|false
```

プリペアドステートメントを実行し、結果セットオブジェクトを返す.

```{warning}
同じステートメントオブジェクトに対して, `excute` すると, 得られる結果セットは独立していないため, そのような場合に, 再び `excute` する際には, `excute` する前に `finalize` することが推奨される.
```

## 例

```php
$sqlite = new SQLite3('mydatabase.db');

$sqlite->exec('CREATE TABLE usertable (id INTEGER, password TEXT)');
$sqlite->exec("INSERT INTO usertable (id, password) VALUES (1, 'abc')");

$stmt = $sqlite->prepare('SELECT password FROM usertable WHERE id=:id');
$stmt->bindValue(':id', 1, SQLITE3_INTEGER);

$result = $stmt->execute();
var_dump($result->fetchArray());
```

**出力：**

```php
array(2) {
  [0]=>
  string(3) "abc"
  ["password"]=>
  string(3) "abc"
}
```

この例は  [SQLite3::prepare](sqlite3_prepare.md) と同様であるため, 説明は省略する.

## 参考文献

- PHP, "SQLite3Stmt::execute", [https://www.php.net/manual/ja/sqlite3stmt.execute.php](https://www.php.net/manual/ja/sqlite3stmt.execute.php), (2024-06-25 参照).

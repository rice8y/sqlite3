# SQLite3Stmt::bindValue

```php
public SQLite3Stmt::bindValue(string|int $param, mixed $value, int $type = SQLITE3_TEXT): bool
```

パラメータの値を変数にバインドする.

## param

バインドする名前付きパラメータ, または位置パラメータ.

## value

変数にバインドする値.

## type

バインドする値のデータ型. データ型は以下の通り.

|データ型|説明|
|---|---|
|SQLITE3_INTEGER|符号付き整数|
|SQLITE3_FLOAT|浮動小数点数|
|SQLITE3_TEXT|文字列|
|SQLITE3_BLOB|bool 値|
|SQLITE3_NULL|NULL 値|

なお, `type` のデフォルトは `SQLITE3_TEXT` . また, PHP 7.0.7 以降では `type` を省略すると, `value` の型から自動的に割り振られる. 具体的な割り振りは以下の通り.

|`value` の型|自動的に割り振られる `type`|
|---|---|
|`bool` , `int`|`SQLITE3_INTEGER`|
|`float`|`SQLITE3_FLOAT`|
|`null`|`SQLITE3_NULL`|
|otherwise|`SQLITE3_TEXT`|

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

- PHP, "SQLite3Stmt::bindValue", [https://www.php.net/manual/ja/sqlite3stmt.bindvalue.php](https://www.php.net/manual/ja/sqlite3stmt.bindvalue.php), (2024-06-25 参照).

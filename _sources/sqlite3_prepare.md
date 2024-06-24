# SQLite3::prepare

```php
public SQLite3::prepare(string $query): SQLite3Stmt|false
```

プリペアドステートメントを作成する.

## query

準備したい SQL クエリ.

## 例

```php
<?php
$sqlite = new SQLite3('mydatabase.db');

$sqlite->exec('CREATE TABLE usertable (id INTEGER, password TEXT)');
$sqlite->exec("INSERT INTO usertable (id, password) VALUES (1, 'abc')");

$stmt = $sqlite->prepare('SELECT password FROM usertable WHERE id=:id');
$stmt->bindValue(':id', 1, SQLITE3_INTEGER);

$result = $stmt->execute();
var_dump($result->fetchArray());
?>
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

この例では, まず, テーブルを作成後, データを挿入している. そして, `prepare` で SQL クエリのプリペアドステートメントを作成し, `usertable` から `id` がプレスホルダー `:id` と一致するカラム `password` を抽出している. その後, `bindValue` でプレスホルダー `:id` に `1` を整数型 (`SQLITE3_INTEGER`) としてバインドしている. 最後に, `excute` でプリペアドステートメントを実行し, 取得した結果セットから `fecthArray` で最初の行を連想配列として取得し,  `var_dump` で表示している.

### 補足

`bindValue` はパラメータの値を変数にバインドし, `excute` はプリペアドステートメントを実行し, 結果セットオブジェクトを返す.

- `bindValue`：[SQLite3Stmt::bindValue](sqlite3_bindvalue.md)
- `excute`：[SQLite3Stmt::execute](sqlite3_excute.md)

## 参考文献

- PHP, "SQLite3::prepare", [https://www.php.net/manual/ja/sqlite3.prepare.php](https://www.php.net/manual/ja/sqlite3.prepare.php), (2024-06-25 参照).
  
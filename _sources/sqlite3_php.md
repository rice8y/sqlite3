# PHP による SQLite3 の基本操作

SQLite3 は, CLI だけでなく他のプログラミング言語のライブラリやバインディングを利用して操作することができる. ここでは, [SQLite CLI の使い方](sqlite3_cli.md) の手順を PHP で行う.

## PHP による SQLite3 の操作例

まず, PHP コードの例を以下に示す.

```php
<?php
$db_file = "mydatabase.db";
$tbl_name = "usertable";

try {
    $sqlite = new SQLite3($db_file);
    $sqlite->enableExceptions(true);
    $sqlite->exec("CREATE TABLE " . $tbl_name . " (id INTEGER PRIMARY KEY AUTOINCREMENT, username TEXT UNIQUE, password TEXT)");
    $sqlite->exec("INSERT INTO " . $tbl_name . " (username, password) VALUES ('testuser', 'testpassword')");
    $sqlite->close();
} catch(Exception $e) {
 echo "Caught exception:" . $e->getMessage();
}
?>
```

上記の例について, 以下で説明する.

### 0. 変数定義

まず, データベースファイル名とテーブル名を変数に格納する.

```php
$db_file = "mydatabase.db";
$tbl_name = "usertable";
```

### 1. データベースへの接続

次に, SQLite3 クラスのインスタンスを生成し, データベースに接続する.

```php
$sqlite = new SQLite3($db_file);
```

この部分は, CLI の

```bash
~$ sqlite3 mydatabase.db
```

または,

```bash
~$ sqlite3
sqlite> .open mydatabase.db
```

の部分に対応する.

### 2. エラー処理

ここでは, 例外処理を有効にしている.

```php
$sqlite->enableExceptions(true);
```

### 3. テーブルの作成

次に, テーブルを作成する.

```php
$sqlite->exec("CREATE TABLE " . $tbl_name . " (id INTEGER PRIMARY KEY AUTOINCREMENT, username TEXT UNIQUE, password TEXT)");
```

この部分は, CLI の

```bash
sqlite> INSERT INTO usertable (username, password) VALUES ('testuser', 'testpassword');
```

の部分に対応する.

### 4. データの挿入

次に, データを挿入する.

```php
$sqlite->exec("INSERT INTO " . $tbl_name . " (username, password) VALUES ('testuser', 'testpassword')");
```

この部分は, CLI の

```bash
sqlite> INSERT INTO usertable (username, password) VALUES ('testuser', 'testpassword');
```

の部分に対応する.

## 5. データベースへの接続終了

最後に, データベースへの接続を切断する.

```php
$sqlite->close();
```

この部分は, CLI の

```bash
sqlite> .exit
```

の部分に対応する.

### 補足

この例では, try-catch ブロックで例外処理を行っている.

## 参考文献

- PHP, "SQLite3", [https://www.php.net/manual/en/book.sqlite3.php](https://www.php.net/manual/en/book.sqlite3.php), (2024-06-25 参照).
  
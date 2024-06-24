# SQLite3::__construct

```php
public SQLite3::__construct(string $filename, int $flags = SQLITE3_OPEN_READWRITE | SQLITE3_OPEN_CREATE, string $encryptionKey = "")
```

SQLite3 オブジェクトを作成し, SQLite3 データベースに接続する.

## filename

データベース接続するファイル名を指定する. インメモリデータベースを使用する場合は, `:memory:` を指定する. なお, `filename` に空文字列を指定すると, プライベートかつ一時的なデータベースファイルが作成され, 接続終了後に自動的に削除される.

## flags

データベースへの接続方法を指定するフラグ. 各フラグの役割は以下の通り.

|フラグ|役割|
|---|---|
|`SQLITE3_OPEN_READONLY`|読み書き専用で接続する|
|`SQLITE3_OPEN_READWRITE`|読み書き共用で接続する|
|`SQLITE3_OPEN_CREATE`|データベースが存在しない場合は作成する|

なお, デフォルトは `SQLITE3_OPEN_READWRITE` .

## encryptionKey

オプションの暗号キー. データベースの暗号化と復号に使用される. 別途, 暗号化モジュールのインストールが必要.

## 例

```php
<?php
$sqlite = new SQLite3('mydatabase.db');
?>
```

```php
<?php
$sqlite = new SQLite3('mydatabase.db', 'SQLITE3_OPEN_CREATE');
?>
```

## 参考文献

- PHP, "SQLite3::__construct", [https://www.php.net/manual/ja/sqlite3.construct.php](https://www.php.net/manual/ja/sqlite3.construct.php), (2024-06-25 参照).
  
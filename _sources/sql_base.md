# SQLite3 の基礎

## データ型

SQLite は他のデータベースエンジンとの互換性を高めるため, 型アフィニティという方法を採用している. ここで, 型アフィニティとは, データベースのカラムにデータを追加する際に, データ型を推測して処理するための方法である. SQLite では, カラムに厳密なデータ型を持たせず, 型アフィニティを持たせることで, データ型を柔軟に扱えるようにしている.

|主なデータ型 (ストレージクラス)|説明|
|---|---|
|INTEGER|符号付き整数値 (8バイトまで格納可能)|
|REAL|8バイトの浮動小数点数|
|TEXT|文字列 (UTF-8, UTF-16BE, または UTF-16LE エンコーディングのデータ)|
|BLOB|バイナリデータ|
|NULL|NULL 値|

|データ型|型アフィニティ|
|---|---|
|INT, INTEGER, TINYINT, SMALLINT, MEDIUMINT, BIGINT, UNSIGNED BIG INT, INT2, INT8|INTEGER|
|CHARACTER(20), VARCHAR(255), VARYING CHARACTER(255), NCHAR(55), NATIVE CHARACTER(70), NVARCHAR(100), TEXT, CLOB|TEXT|
|BLOB, *no datatype specified*|BLOB|
|REAL, DOUBLE, DOUBLE PRECISION, FLOAT|REAL|
|NUMERIC, DECIMAL(10,5), BOOLEAN, DATE, DATETIME|NUMERIC|

## フィールド制約

フィールド制約を以下に示す.

|フィールド制約|説明|
|---|---|
|PRIMARY KEY|一意の識別子を持つフィールドを定義 (テーブルに1つまで)|
|AUTOINCREMENT|自動インクリメント|
|UNIQUE|一意性を保証 (重複防止)|
|NOT NULL|NULL 値を禁止|
|CHECK|特定の条件を満たすことを保証|
|DEFAULT|NULL の場合にセット|
|FOREIGN KEY|外部キー制約|

なお, `FOREIGN KEY` 制約を付加する際には, `PRAGMA foreign_keys = ON;` を実行して有効化する必要がある. 実際には, 有効化しなくても制約を付加できるが, エラーが発生しないため有効化することを推奨する.

### 例

```sql
CREATE TABLE table_name1 (
  id INTEGER PRIMARY KEY AUTOINCREMENT,
  name TEXT NOT NULL DEFAULT '' CHECK(name IN ('hoge', 'fuga')),
  param1 TEXT UNIQUE,
  param2 INTEGER REFERENCES table_name2(id)
);
```

なお, `AUTOINCREMENT` は `PRIMARY KEY` の後に置かなければならない. また, 複数のカラムに `UNIQUE` 制約を付加したい場合は, `CREATE` 文 の最後に `UNIQUE ({column1, column2, ...})` をつける.

## 参考文献

- SQLite, "Datatypes In SQLite", [https://sqlite.org/datatype3.html](https://sqlite.org/datatype3.html), (2024-06-25 参照).
  
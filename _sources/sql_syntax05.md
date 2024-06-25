# その他の操作

## ビューの作成

```sql
CREATE VIEW view_name AS SELECT name FROM column1 WHERE condition;
```

## ビューからデータを抽出

```sql
SELECT * FROM view_name;
```

## ビューの削除

```sql
DROP VIEW IF EXISTS view_name;
```

```{note}
ビューからデータを抽出することは出来るが, データを追加・削除することはできない.
```

## トリガーの作成

```sql
CREATE TRIGGER trigger_name [ BEFORE | AFTER | INSTEAD OF ]
 { DELETE | UPDATE [ OF column1, column2, ... ] | INSERT } ON table_name
 [ FOR EACH ROW | FOR EACH STATEMENT ]
 [ WHERE condition ]
 BEGIN
  sql_statement1;
  sql_statement2;
  ...
 END;
```

## トリガーの削除

```sql
DROP TRIGGER IF EXISTS trigger_name;
```

[ ] で囲まれた部分は省略可能.

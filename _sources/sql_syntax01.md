# テーブル操作

## テーブルの作成

```sql
CREATE TABLE table_name (colmun1 datatype, colmun2 datatype, ...);
```

## テーブルの削除

```sql
DROP TABLE IF EXISTS table_name;
```

## テーブルの変更

### カラムの追加

```sql
ALTER TABLE table_name ADD COLUMN new_column_name datatype;
```

## テーブル名の変更

```sql
ALTER TABLE old_table_name RENAME TO new_table_name;
```

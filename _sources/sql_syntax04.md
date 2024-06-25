# トランザクション操作

## トランザクションの開始

```sql
BEGIN [ DEFERRED | IMMEDIATE | EXCLUSIVE ] [ TRANSACTION [ TransactionName ] ];
```

[ ] で囲まれた部分は省略できる. トランザクションの種類は以下の通り.

|トランザクションの種類|説明|
|---|---|
|DEFERRED|共有ロック / 予約ロック|
|EXCLUSIVE|排他ロック|
|IMMEDIATE|予約ロック|

なお, トランザクションのデフォルトは `DEFERRED` .

## トランザクションを終了し, 変更内容を更新

```sql
COMMIT [ TRANSACTION [ TransactionName ] ];
```

[ ] で囲まれた部分は省略できる.

## トランザクションを終了し, 変更内容を破棄

```sql
ROLLBACK [ TRANSACTION [ TransactionName ] ];
```

[ ] で囲まれた部分は省略できる.

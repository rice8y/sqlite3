# SQLite3 CLI の使い方

## 準備

まず, SQLite3 がインストールされているかを確認する. 以下のようにバージョン情報が表示されればOK.

```bash
~$ sqlite3 --version
3.37.2 2022-01-06 13:25:41 872ba256cbf61d9290b571c0e6d82a20c224ca3ad82971edc46b29818d5dalt1
```

次に, 公開ディレクトリに移動する. ここでは, SQLite3 のテスト用ディレクトリ `test` を作成し, その配下で以降の操作を行う.

```bash
~$ cd public_html/pblone
~/public_html/pblone$ mkdir sqltest
~/public_html/pblone$ cd sqltest
~/public_html/pblone/sqltest$
```

## CLI の起動

まず, `sqlite3` で SQLite3 CLI を起動する. ここでは, CLI が起動しただけで, データベースには接続されていない点に注意.

```bash
~/public_html/pblone/sqltest$ sqlite3
SQLite version 3.37.2 2022-01-06 13:25:41
Enter ".help" for usage hints.
Connected to a transient in-memory database.
Use ".open FILENAME" to reopen on a persistent database.
```

ここでは, CLI が起動しただけで, データベースには接続されていない点に注意.

## データベースファイル (.db) の作成

次に, データベースファイル (.db) を作成する. 具体的には, `.open` でデータベースファイルを作成する. なお, `.open` では, 指定したデータベースファイルがカレントディレクトリに存在しなければ新たにデータベースファイルが作成され, 存在すればそのデータベースファイルが開かれる (接続される).

```bash
sqlite> .open mydatabase.db
```

また, CLI 起動時に `sqlite3 (ファイル名).db` とすることで, データベースを指定して CLI を起動することもできる.

```bash
~/public_html/pblone/sqltest$ sqlite3 mydatabase.db
SQLite version 3.37.2 2022-01-06 13:25:41
Enter ".help" for usage hints.
```

この操作でも, 指定したデータベースファイルが存在しなければ新たにデータベースファイルが作成され, 存在すればそのデータベースファイルが開かれる (接続される).

## テーブルの作成

次に, テーブルを作成する. テーブル作成の構文については後述.

```bash
sqlite> CREATE TABLE usertable (id INTEGER PRIMARY KEY AUTOINCREMENT, username TEXT UNIQUE, password TEXT);
```

ここでは, `usertable` という名のテーブルを作成し, `id` , `username` , `password` という3つのフィールドを持つようにしている.

## データの挿入

次に, データを挿入する. この構文についても後述.

```bash
sqlite> INSERT INTO usertable (username, password) VALUES ('testuser', 'testpassword');
```

ここでは, `username` に "testuser", `password` に "testpassword" を挿入している. なお, `id` は `AUTOINCREMENT` であり, 自動で付加される.

テーブルの内容は以下のようにして確認できる.

```bash
sqlite> SELECT * FROM usertable;
1|testuser|testpassword
```

また, `.headers on` を実行することで, テーブルのカラム名が表示されるようになる.

```bash
sqlite> .headers on
sqlite> SELECT * FROM usertable;
id|username|password
1|testuser|testpassword
```

## CLI の終了

CLI は, `.exit` または `.ex` で終了できる. `Ctrl+D` でも可.

```bash
sqlite> .exit
~/public_html/pblone/sqltest$
```
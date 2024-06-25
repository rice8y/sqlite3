# 演算子

## 算術演算子

### 加算演算子 `+`

```sql
SELECT 2 + 2 AS result;  -- 4
```

### 減算演算子 `-`

```sql
SELECT 5 - 3 AS result;  -- 2
```

### 乗算演算子 `*`

```sql
SELECT 4 * 5 AS result;  -- 20
```

### 除算演算子 `/`

```sql
SELECT 10 / 2 AS result;  -- 5
```

### 剰余演算子 `%`

```sql
SELECT 7 % 3; AS result;  -- 1
```

## 比較演算子

### 等しい `=` , `==`

```sql
SELECT 1 = 2 AS result;  -- FALSE
SELECT 1 == 1 AS result;  -- TRUE
SELECT * FROM users WHERE age = 30;
SELECT * FROM users WHERE age == 25;
```

### 等しくない `!=` , `<>`

```sql
SELECT 1 != 2 AS result;  -- TRUE
SELECT 1 <> 2 AS result;  -- TRUE
SELECT * FROM users WHERE age != 30;
SELECT * FROM users WHERE age <> 25;
```

### より大きい `>`

```sql
SELECT 1 > 2 AS result;  -- FALSE
SELECT * FROM users WHERE age > 30;
```

### より小さい `<`

```sql
SELECT 1 < 2 AS result;  -- TRUE
SELECT * FROM users WHERE age < 30;
```

### 以上 `>=`

```sql
SELECT 1 >= 2 AS result;  -- FALSE
SELECT * FROM users WHERE age >= 30;
```

### 以下 `<=`

```sql
SELECT 1 <= 2 AS result;  -- TRUE
SELECT * FROM users WHERE age <= 30;
```

## 論理演算子

### 論理積 `AND`

```sql
SELECT TRUE AND TRUE AS result;  -- TRUE
SELECT TRUE AND FALSE AS result;  -- FALSE
SELECT * FROM users WHERE age > 30 AND city = 'Tokyo';
```

### 論理和 `OR`

```sql
SELECT TRUE OR FALSE AS result;  -- TRUE
SELECT * FROM users WHERE age > 30 OR city = 'Tokyo';
```

### 否定 `NOT`

```sql
SELECT NOT TRUE AS result;  -- FALSE
SELECT * FROM users WHERE NOT age = 30;
```

## ビット演算子

### AND `&`

```sql
SELECT 5 & 3 AS result;  -- 1
SELECT permissions & 1 FROM users;
```

### OR `|`

```sql
SELECT 5 | 3 AS result;  -- 7
SELECT permissions | 2 FROM users;
```

### 左シフト `<<`

```sql
SELECT 1 << 2 AS result;  -- 4
SELECT id << 1 FROM users;
```

### 右シフト `>>`

```sql
SELECT 4 >> 2 AS result;  -- 1
SELECT id >> 1 FROM users;
```

### ビット反転 `~`

```sql
SELECT ~1 AS result;  -- -2
SELECT ~id FROM users;
```

## その他の演算子

### 文字列結合 `||`

```sql
SELECT 'Hello, ' || 'World!' AS result;  -- Hello, World!
SELECT first_name || ' ' || last_name FROM users;
```

### リストに含まれている `IN`

```sql
SELECT * FROM users WHERE age IN (25, 30, 35);
```

`IN` では指定したリストのデータの内, いずれかと一致すればOK.

### 範囲内にある `BETWEEN`

```sql
SELECT * FROM users WHERE age BETWEEN 20 AND 30;
```

`BETWEEN` は閉区間を意味する. 上記の例では, $20\leq \mathrm{age}\leq 30$ .

### NULL である `IS NULL`

```sql
SELECT * FROM users WHERE age IS NULL;
```

### NULL でない `IS NOT NULL`

```sql
SELECT * FROM users WHERE age IS NOT NULL;
```

### パターンに一致する `LIKE`

```sql
SELECT * FROM users WHERE name LIKE 'A%';
```

ワイルドカードを以下に示す.

|ワイルドカード|説明|
|---|---|
|%|任意の文字列 (長さ0以上)|
|_|任意の1文字|

`LIKE` の例を以下に示す.

|`LIKE` の例|説明|
|---|---|
|`LIKE 'A%'`|Aで始まる任意の長さの文字列|
|`LIKE '%A'`|Aで終わる任意の長さの文字列|
|`LIKE '%A%'`|任意の位置にAを含む任意の長さの文字列|
|`LIKE '_A%'`|Aが2文字目である任意の長さの文字列|
|`LIKE 'A_'`|Aで始まり2文字目が任意の1文字の文字列|

### パターンに一致する (UNIX の glob パターン) `GLOB`

```sql
SELECT * FROM users WHERE name GLOB 'A*';
```

ワイルドカードを以下に示す.

|ワイルドカード|説明|
|---|---|
|*|任意の文字列 (長さ0以上)|
|?|任意の1文字|

`GLOB` の例を以下に示す.

|`GLOB` の例|説明|
|---|---|
|`GLOB 'A*'`|Aで始まる任意の長さの文字列|
|`GLOB '*A'`|Aで終わる任意の長さの文字列|
|`GLOB '*A*'`|任意の位置にAを含む任意の長さの文字列|
|`GLOB '?A*'`|Aが2文字目である任意の長さの文字列|
|`GLOB 'A?'`|Aで始まり2文字目が任意の1文字の文字列|

### 特殊文字のエスケープ `ESCAPE`

```sql
SELECT * FROM users WHERE name LIKE 'A\%%' ESCAPE '\';
```

### 正規表現に一致する `REGEXP`

```sql
SELECT * FROM users WHERE name REGEXP '^[A-Z]+$';
```

### 存在する `EXISTS`

```sql
SELECT column1 FROM table1 WHERE EXISTS (SELECT * FROM table2);
```

### DESCRIBE TABLE

- 테이블 목록

```sql
SELECT * FROM tab;
```

```sql
SELECT * FROM tabs;
```

- 모든 테이블의 구조

```sql
SELECT * FROM col;
```

```sql
SELECT * FROM cols;
```

```sql
SELECT * FROM user_tab_columns;
```

- 테이블 스키마

```sql
SELECT * FROM col WHERE tname='table_name';
```

```sql
SELECT * FROM cols WHERE table_name = 'table_name';
```

```sql
SELECT * FROM user_tab_columns WHERE table_name='table_name';
```

```sql
DESCRIBE table_name;
```

```sql
DESC table_name;
```

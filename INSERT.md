### INSERT

- column 명을 사용하는 경우

```sql
INSERT INTO table_name ( column_name1
                                             , column_name2
                                             , column_name3
                                             )
                              VALUES ( input1
                                             , input2
                                             , input3
                                             )
;
```

- column 명을 사용하지 않는 경우
  - 모든 column에 대해 정의하는 경우 사용 가능

```sql
INSERT INTO table_name
VALUES (input1
       ,input2
       ,input3
       )
;
```

- 다중 입력

```sql
INSERT INTO table_name
                        (column_name1, column_name2)
         VALUES (input11, input12)
                     , (input21, input22)
                  , (input31, input32) 
;
```

```sql
INSERT INTO people
                        (first_name, last_name, age)
          VALUES ('Tina', 'Belcher', 13)
;
```

```sql
INSERT INTO people
                        (first_name, last_name, age)
         VALUES ('Linda', 'Belcher', 45)
                    , ('Phillip', 'Frond', 38)
                    , ('Calvin', 'Fischoeder', 70)
;
```

## LPAD, RPAD

- Padding으로 문자열의 자릿수를 맞추는 함수
- LPAD : 왼쪽에 특정 문자로 자릿수를 채우는 함수
- RPAD : 오른쪽에 특정 문자로 자릿수를 채우는 함수

```sql
WITH EMP AS (
    SELECT '7839' EMPNO, 'JAMES' ENAME, '30' DEPTNO FROM DUAL
)

SELECT EMPNO
    , ENAME
    , DEPTNO
    , LPAD(DEPTNO, 5) "1"
    , LPAD(DEPTNO, 5, ' ') "2"
    , LPAD(DEPTNO, 5, '0') "3"
    , LPAD(DEPTNO, 5, 'A') "4"
FROM EMP
```

| EMPNO | ENAME | DEPTNO | 1   | 2   | 3     | 4     |
| ----- | ----- | ------ | --- | --- | ----- | ----- |
| 7839  | JAMES | 30     | 30  | 30  | 00030 | AAA30 |

```sql
WITH EMP AS (
    SELECT '7839' EMPNO, 'JAMES' ENAME, '30' DEPTNO FROM DUAL
)

SELECT EMPNO
    , ENAME
    , DEPTNO
    , RPAD(DEPTNO, 5) "1"
    , RPAD(DEPTNO, 5, ' ') "2"
    , RPAD(DEPTNO, 5, '0') "3"
    , RPAD(DEPTNO, 5, 'A') "4"
FROM EMP
```

| EMPNO | ENAME | DEPTNO | 1   | 2   | 3     | 4     |
| ----- | ----- | ------ | --- | --- | ----- | ----- |
| 7839  | JAMES | 30     | 30  | 30  | 30000 | 30AAA |

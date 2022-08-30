### CASE WHEN THEN END

```sql
WITH emp AS (
    SELECT 7839 empno, 'KING'   ename, 'PRESIDENT' job, NULL mgr, TO_DATE('1981-11-17','yyyy-mm-dd') hiredate, 5000 sal, NULL comm, '10' deptno FROM dual UNION ALL
    SELECT 7698 empno, 'BLAKE'  ename, 'MANAGER'   job, 7839 mgr, TO_DATE('1981-05-01','yyyy-mm-dd') hiredate, 2850 sal, NULL comm, '30' deptno FROM dual UNION ALL
    SELECT 7782 empno, 'CLARK'  ename, 'MANAGER'   job, 7839 mgr, TO_DATE('1981-06-09','yyyy-mm-dd') hiredate, 2450 sal, NULL comm, '10' deptno FROM dual UNION ALL
    SELECT 7566 empno, 'JONES'  ename, 'MANAGER'   job, 7839 mgr, TO_DATE('1981-04-02','yyyy-mm-dd') hiredate, 2975 sal, NULL comm, '20' deptno FROM dual UNION ALL
    SELECT 7788 empno, 'SCOTT'  ename, 'ANALYST'   job, 7566 mgr, TO_DATE('1987-04-19','yyyy-mm-dd') hiredate, 3000 sal, NULL comm, '20' deptno FROM dual UNION ALL
    SELECT 7902 empno, 'FORD'   ename, 'ANALYST'   job, 7566 mgr, TO_DATE('1981-12-03','yyyy-mm-dd') hiredate, 3000 sal, NULL comm, '20' deptno FROM dual UNION ALL
    SELECT 7369 empno, 'SMITH'  ename, 'CLERK'     job, 7902 mgr, TO_DATE('1980-12-17','yyyy-mm-dd') hiredate, 800  sal, NULL comm, '20' deptno FROM dual UNION ALL
    SELECT 7499 empno, 'ALLEN'  ename, 'SALESMAN'  job, 7698 mgr, TO_DATE('1981-02-20','yyyy-mm-dd') hiredate, 1600 sal, 300  comm, '30' deptno FROM dual UNION ALL
    SELECT 7521 empno, 'WARD'   ename, 'SALESMAN'  job, 7698 mgr, TO_DATE('1981-02-22','yyyy-mm-dd') hiredate, 1250 sal, 500  comm, '30' deptno FROM dual UNION ALL
    SELECT 7654 empno, 'MARTIN' ename, 'SALESMAN'  job, 7698 mgr, TO_DATE('1981-09-28','yyyy-mm-dd') hiredate, 1250 sal, 1400 comm, '30' deptno FROM dual UNION ALL
    SELECT 7844 empno, 'TURNER' ename, 'SALESMAN'  job, 7698 mgr, TO_DATE('1981-09-08','yyyy-mm-dd') hiredate, 1500 sal, 0    comm, '30' deptno FROM dual UNION ALL
    SELECT 7876 empno, 'ADAMS'  ename, 'CLERK'     job, 7788 mgr, TO_DATE('1987-05-23','yyyy-mm-dd') hiredate, 1100 sal, NULL comm, '20' deptno FROM dual UNION ALL
    SELECT 7900 empno, 'JAMES'  ename, 'CLERK'     job, 7698 mgr, TO_DATE('1981-12-03','yyyy-mm-dd') hiredate, 950  sal, NULL comm, '30' deptno FROM dual UNION ALL
    SELECT 7934 empno, 'MILLER' ename, 'CLERK'     job, 7782 mgr, TO_DATE('1982-01-23','yyyy-mm-dd') hiredate, 1300 sal, NULL comm, '10' deptno FROM dual
)
```

```sql
SELECT empno
    , deptno
        , CASE WHEN deptno = '10' THEN 'New York'
                     WHEN deptno = '20' THEN 'Dallas'
                     ELSE 'Unknown'
            END AS loc_name
FROM emp
WHERE job = 'MANAGER'
```

| EMPNO | DEPTNO | LOC_NAME |
| ----- | ------ | -------- |
| BLAKE | 30     | Unknown  |
| CLARK | 10     | New York |
| JONES | 20     | Dallas   |

```sql
SELECT empno
    , deptno
    , CASE deptno 
            WHEN '10' THEN 'New York'
                WHEN '20' THEN 'Dallas'
                ElSE 'Unknown'
            END AS loc_name
FROM emp
WHERE job = 'MANAGER'
```

| EMPNO | DEPTNO | LOC_NAME |
| ----- | ------ | -------- |
| BLAKE | 30     | Unknown  |
| CLARK | 10     | New York |
| JONES | 20     | Dallas   |

```sql
SELECT empno
    , deptno
    , CASE deptno 
            WHEN '10' THEN 'New York'
                WHEN '20' THEN 'Dallas'
            **END AS loc_name
FROM emp
WHERE job = 'MANAGER
```

| EMPNO | DEPTNO | LOC_NAME |
| ----- | ------ | -------- |
| BLAKE | 30     |          |
| CLARK | 10     | New York |
| JONES | 20     | Dallas   |

```sql
SELECT ename
    , sal
    , CASE WHEN sal >= 2900 THEN '1등급'
           WHEN sal >= 2700 THEN '2등급'
               WHEN sal >= 2000 THEN '3등급'
          END AS sal_grade
FROM emp
WHERE job = 'MANAGER'
AND (CASE WHEN sal >= 2900 THEN 1
                    WHEN sal >= 2700 THEN 2
                    WHEN sal >= 2000 THEN 3
         END) = 1
```

| ENAME | SAL  | SAL_GRADE |
| ----- | ---- | --------- |
| JONES | 2975 | 1등급       |

### CASE WHEN THEN END 중첩

```sql
WITH emp AS (
    SELECT 7839 empno, 'KING'   ename, 'PRESIDENT' job, NULL mgr, TO_DATE('1981-11-17','yyyy-mm-dd') hiredate, 5000 sal, NULL comm, '10' deptno FROM dual UNION ALL
    SELECT 7698 empno, 'BLAKE'  ename, 'MANAGER'   job, 7839 mgr, TO_DATE('1981-05-01','yyyy-mm-dd') hiredate, 2850 sal, NULL comm, '30' deptno FROM dual UNION ALL
    SELECT 7782 empno, 'CLARK'  ename, 'MANAGER'   job, 7839 mgr, TO_DATE('1981-06-09','yyyy-mm-dd') hiredate, 2450 sal, NULL comm, '10' deptno FROM dual UNION ALL
    SELECT 7566 empno, 'JONES'  ename, 'MANAGER'   job, 7839 mgr, TO_DATE('1981-04-02','yyyy-mm-dd') hiredate, 2975 sal, NULL comm, '20' deptno FROM dual UNION ALL
    SELECT 7788 empno, 'SCOTT'  ename, 'ANALYST'   job, 7566 mgr, TO_DATE('1987-04-19','yyyy-mm-dd') hiredate, 3000 sal, NULL comm, '20' deptno FROM dual UNION ALL
    SELECT 7902 empno, 'FORD'   ename, 'ANALYST'   job, 7566 mgr, TO_DATE('1981-12-03','yyyy-mm-dd') hiredate, 3000 sal, NULL comm, '20' deptno FROM dual UNION ALL
    SELECT 7369 empno, 'SMITH'  ename, 'CLERK'     job, 7902 mgr, TO_DATE('1980-12-17','yyyy-mm-dd') hiredate, 800  sal, NULL comm, '20' deptno FROM dual UNION ALL
    SELECT 7499 empno, 'ALLEN'  ename, 'SALESMAN'  job, 7698 mgr, TO_DATE('1981-02-20','yyyy-mm-dd') hiredate, 1600 sal, 300  comm, '30' deptno FROM dual UNION ALL
    SELECT 7521 empno, 'WARD'   ename, 'SALESMAN'  job, 7698 mgr, TO_DATE('1981-02-22','yyyy-mm-dd') hiredate, 1250 sal, 500  comm, '30' deptno FROM dual UNION ALL
    SELECT 7654 empno, 'MARTIN' ename, 'SALESMAN'  job, 7698 mgr, TO_DATE('1981-09-28','yyyy-mm-dd') hiredate, 1250 sal, 1400 comm, '30' deptno FROM dual UNION ALL
    SELECT 7844 empno, 'TURNER' ename, 'SALESMAN'  job, 7698 mgr, TO_DATE('1981-09-08','yyyy-mm-dd') hiredate, 1500 sal, 0    comm, '30' deptno FROM dual UNION ALL
    SELECT 7876 empno, 'ADAMS'  ename, 'CLERK'     job, 7788 mgr, TO_DATE('1987-05-23','yyyy-mm-dd') hiredate, 1100 sal, NULL comm, '20' deptno FROM dual UNION ALL
    SELECT 7900 empno, 'JAMES'  ename, 'CLERK'     job, 7698 mgr, TO_DATE('1981-12-03','yyyy-mm-dd') hiredate, 950  sal, NULL comm, '30' deptno FROM dual UNION ALL
    SELECT 7934 empno, 'MILLER' ename, 'CLERK'     job, 7782 mgr, TO_DATE('1982-01-23','yyyy-mm-dd') hiredate, 1300 sal, NULL comm, '10' deptno FROM dual
)
```

```sql
SELECT ename
     , sal
     , deptno
     , CASE WHEN deptno = '10' THEN 
                 CASE WHEN sal >= 2000 THEN '1등급'
                      WHEN sal >= 1500 THEN '2등급'
                      WHEN sal >= 1000 THEN '3등급'
                 END     
            WHEN deptno = '20' THEN 
                 CASE WHEN sal >= 3000 THEN '1등급'
                      WHEN sal >= 2500 THEN '2등급'
                      WHEN sal >= 2000 THEN '3등급'
                 END            
            WHEN deptno = '30' THEN 
                 CASE WHEN sal >= 2500 THEN '1등급'
                      WHEN sal >= 2000 THEN '2등급'
                      WHEN sal >= 1500 THEN '3등급'
                 END            
       END AS sal_grade
  FROM emp
 WHERE job = 'MANAGER'
;
```

| ENAME | SAL  | DEPTNO | SAL_GRADE |
| ----- | ---- | ------ | --------- |
| BLAKE | 2850 | 30     | 1등급       |
| CLARK | 2450 | 10     | 1등급       |
| JONES | 2975 | 20     | 2등급       |

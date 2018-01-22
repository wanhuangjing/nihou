##### mysql使用in查询，按照期望的顺序输出结果，可以使用field函数
```sql
UPDATE ec_student set teacherid = 5 WHERE id in(1,2,3) ORDER BY FIELD (id,1,2,3)
```

#### Case具有两种格式。简单Case函数和Case搜索函数。
* 简单Case函数
  ```sql
  CASE sex
           WHEN '1' THEN '男'
           WHEN '2' THEN '女'
  ELSE '其他' END
  ```
* Case搜索函数
  ```sql
  CASE WHEN sex = '1' THEN '男'
           WHEN sex = '2' THEN '女'
  ELSE '其他' END
  ```

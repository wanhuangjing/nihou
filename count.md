1.count()函数是用来统计表中记录的一个函数，返回匹配条件的行数。



2.count()语法：

（1）count(*)---包括所有列，返回表中的记录数，相当于统计表的行数，在统计结果的时候，不会忽略列值为NULL的记录。

（2）count(1)---忽略所有列，1表示一个固定值，也可以用count(2)、count(3)代替，在统计结果的时候，不会忽略列值为NULL的记录。

（3）count(列名)---只包括列名指定列，返回指定列的记录数，在统计结果的时候，会忽略列值为NULL的记录（不包括空字符串和0），即列值为NULL的记录不统计在内。

（4）count(distinct 列名)---只包括列名指定列，返回指定列的不同值的记录数，在统计结果的时候，在统计结果的时候，会忽略列值为NULL的记录（不包括空字符串和0），即列值为NULL的记录不统计在内。



3.count(*)&count(1)&count(列名)执行效率比较：

（1）如果列为主键，count(列名)效率优于count(1)

（2）如果列不为主键，count(1)效率优于count(列名)

（3）如果表中存在主键，count(主键列名)效率最优

（4）如果表中只有一列，则count(*)效率最优

（5）如果表有多列，且不存在主键，则count(1)效率优于count(*)



4.因为count(*)和count(1)统计过程中不会忽略列值为NULL的记录，所以可以通过以下两种方式来统计列值为NULL的记录数:

（1）select count(*) from table where is_active is null;
（2）select count(1) from table where is_active is null;


5.特例：

（1）select count('') from table;-返回表的记录数
（2）select count(0) from table;-返回表的记录数
（3）select count(null) from table;-返回0
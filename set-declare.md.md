##### 在存储过程中常看到declare定义的变量和@set定义的变量。简单的来说，declare定义的类似是局部变量，@set定义的类似全局变量。

* declare定义的变量类似java类中的局部变量，仅在类中生效。即只在存储过程中的begin和end之间生效。
* @set定义的变量，叫做会话变量，也叫用户定义变量，在整个会话中都起作用(比如某个应用的一个连接过程中)，即这个变量可以在被调用的存储过程或者代码之间共享数据。如何理解呢？可以看下面这个简单例子，很好理解。

#### 例子
1. 先执行下面脚本，创建一个存储过程，分别有declare形式的变量和@set形式的变量

  ```sql
  DROP PROCEDURE IF EXISTS temp;
  DELIMITER //
  CREATE PROCEDURE temp()
  BEGIN
    DECLARE a INT DEFAULT 1;

    SET a=a+1;
    SET @b=@b+1;
    SELECT a,@b;

  END
  //
  DELIMITER ;
  DROP PROCEDURE IF EXISTS temp;
  DELIMITER //
  CREATE PROCEDURE temp()
  BEGIN
    DECLARE a INT DEFAULT 1;

    SET a=a+1;
    SET @b=@b+1;
    SELECT a,@b;

  END
  //
  DELIMITER ;
  ```
2. 接着为b变量初始化。

  ```sql
  SET @b=1;
  ```

2. 然后重复调用这个存储过程。

  ```sql
  CALL temp();
  ```

2. 会发现a的值不改变，而b的值会一直增加。

##### 所以，总结起来就是开头那句话，declare定义的类似是局部变量，@set定义的类似全局变量。

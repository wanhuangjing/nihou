### ![](http://es6.ruanyifeng.com/#docs/let)
#### let命令

##### let所声明的变量，只在`let`命令所在的代码块内有效

```javascript
{
 let a = 10;
 var b = 1;
}
a//ReferenceError: a is not defined
b//1
```
```javascript
for (let i = 0; i < 10; i++) {
 console.log(i)
}
```

##### 上面的代码中，变量`i`是`let`声明的，所以每一次循环的`i`其实都是一个新的变量，但是javascript引擎内部会记住上一轮循环的值，初始化本轮的变量`i`时，就在上一轮循环基础上进行计算,`for`循环中，设置循环变量的那部分是一个父作用域，而循环内部是一个单独的子作用域




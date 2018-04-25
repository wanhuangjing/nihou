#### let命令
##### let所声明的变量，只在`let`命令所在的代码块内有效
`
{
 let a = 10;
 var b = 1;
}
a//ReferenceError: a is not defined
b//1
`

##### `var_export`此函数返回关于传递给该函数的变量的结构信息，它和 `var_dump()`  类似，不同的是其返回的表示是合法的 PHP 代码。`var_export()` 的第二个参数需要设置为 true 才表示取得返回值。要不然是直接输出

```PHP
$arr =  Array(
	'as'=>'123',
	'ad'=> 'asd'
);
print_r(print_r($arr,true));
var_export($arr);exit;

Array
(
    [as] => 123
    [ad] => asd
)
array (
  'as' => '123',
  'ad' => 'asd',
)
```

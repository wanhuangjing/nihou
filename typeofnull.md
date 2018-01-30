##### 在javascript中，`typeof null`的结果是object，这会使错误的认为null是一个对象（但是它不是一个对象，它是一个原始值）。不幸的是，这是一个不能被修复的bug，因为修复后，会破坏现有的代码。那么，让我们一起探索一下这个bug的来历吧

##### 这个bug是第一个版本javascript遗留下来的问题，在第一个版本中，数据是以32位存储的，其中（1-3）位是用来标志数据类型的标志位，其余是真正的数值。标志位储存在低位。（右边是低位，左边是高位），下面是5中数据类型的标志位
* 000：对象
* 1：整型 31位的带符号的整数
* 010：双精度浮点数
* 100：字符串  
* 110：布尔值
##### 也就是说，最低位是1的，标志位只有1位，或者，最低位是0的，标志位占了3位，有了两个额外的位，一共4种类型
##### 两种特殊的数值
* undefined(JSVAL_VOID)，它的值是-2^30(超出了整数范围)
* null(JSVAL_NULL),机器码空指针，或者一个对象的标志位加上为0的引用

##### 很明显这就是为什么`typeof null`的值是object。它检查了null的标志位，并且标志位表明它是个对象，下面是typeof的源码实现
```c
JS_PUBLIC_API(JSType)
JS_TypeOfValue(JSContext *cx, jsval v)
{
    JSType type = JSTYPE_VOID;
    JSObject *obj;
    JSObjectOps *ops;
    JSClass *clasp;

    CHECK_REQUEST(cx);
    if (JSVAL_IS_VOID(v)) {  // (1)
        type = JSTYPE_VOID;
    } else if (JSVAL_IS_OBJECT(v)) {  // (2)
        obj = JSVAL_TO_OBJECT(v);
        if (obj &&
            (ops = obj->map->ops,
             ops == &js_ObjectOps
             ? (clasp = OBJ_GET_CLASS(cx, obj),
                clasp->call || clasp == &js_FunctionClass) // (3,4)
             : ops->call != 0)) {  // (3)
            type = JSTYPE_FUNCTION;
        } else {
            type = JSTYPE_OBJECT;
        }
    } else if (JSVAL_IS_NUMBER(v)) {
        type = JSTYPE_NUMBER;
    } else if (JSVAL_IS_STRING(v)) {
        type = JSTYPE_STRING;
    } else if (JSVAL_IS_BOOLEAN(v)) {
        type = JSTYPE_BOOLEAN;
    }
    return type;
}
```
##### 上面的代码步骤是这样的
* 注释（1）：首先会检测数据是否是undefined（VOID），通过比较值是否相等
```c
 #define JSVAL_IS_VOID(v)  ((v) == JSVAL_VOID)
```
* 注释（2）：数据是否有对象标志位。如果它是可调用的，或者说通过内部属性[[Class]]可以表明它是一个函数。否者它就是一个对象。这也就是`typeof null`的执行结果。
* 随后是针对数字、字符串和布尔值的检测。这里并没有明确的检测null，本身应该存在一个类似检测undefined一样的方法，来检测null，但是事实证明它并没有
```c
#define JSVAL_IS_NULL(v)  ((v) == JSVAL_NULL)
```
##### 这看起来像是一个很明显的bug，但是不要忘了Javascript的第一个版本花费了很少的时间完成的。
##### [原文地址](http://www.2ality.com/2013/10/typeof-null.html)

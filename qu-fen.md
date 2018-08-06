# [Chrome控制台选择器简介](https://www.cnblogs.com/aqiongbei/p/7577755.html)

Chrome的控制台是支持用`$`来获取元素的，这点可能是很多人不知道的。本篇文章将会简单介绍怎样更好的来使用这种快捷方式来获取元素。

## 判断当前窗口的$是来自谁的 {#判断当前窗口的是来自谁的}

我们知道`jQ`里面经常使用`$`来进行元素选择，Chrome也提供`$`来进行元素选择，而很多页面都会引入`jQ`，但是由于这两种方式返回的结果是不一样的。所以我们要区分一下这个`$`是由谁提供的，以便进行下一步操作。  
做区分的方式很简单，在`console`中输入`$`，然后通过输出的信息来判断这个`$`来自那里。一般做如下区分：

## 来自Chrome提供的$ {#来自chrome提供的}

如果这个`$`是由Chrome提供的，那么会有如下提示：

```
ƒ $(selector, [startNode]) { [Command Line API] }
```

## 来自jQ的$ {#来自jq的}

而如果这个`$`是由`jQ`提供的则返回如下信息

```
ƒ (e,t){
return
new
 s.fn.init(e,t,r)}
```

或者是

```
ƒ ( selector, context ) {

        
// The jQuery object is actually just the init constructor 'enhanced'
// Need init if jQuery is called (just allow error to be thrown if not included)
return
new
 jQuery…
```

## Chrome提供的$的用法 {#chrome提供的的用法}

上面我们已经对Chrome提供的`$`与jQ提供的`$`做出了区分。jQ的`$`大家很熟悉，不用多说，我们主要介绍Chrome提供的`$`的用法，以及与jQ提供的`$`的区别。  
Chrome的`$`其实调用的是`querySelector()`。所以`$`的使用很简单

```
$(
'#query'
); 
// 获取id为query的一个元素

$(
'.nav'
); 
// 获取class包含nav的一个元素

$(
'div'
); 
// 获取tagName为div的一个元素
```

除了可以使用`$`,我们还可以使用`$$`。`$$`其实调用的是`querySelectorAll()`，所以通过`$$`我们可以获取到一个`NodeList`

```
$(
'.nav'
); 
// 获取calss包含nav的所有元素

$(
'div'
); 
// 获取tagName为div的所有元素
```

除了上面提到的，我们可以使用`$x`来通过`xPath`选择元素。

```
$x(
'html/body/div'
) 
// 获取html下的直接子元素body下的直接子元素div
```

此外，我们需要注意的是:

> 通过`jQ`的`$`获取到的是一个`jQ`对象。这点我们可以通过在支持的`jQ`的页面中打开`Console`输入下面的语句来确认。
>
> ```
> $(
> 'a'
> ) 
> instanceof
> document
> // true
> ```
>
> 而由于Chrome提供的`$`是调用的`querySelector`，所以通过Chrome的`$`到的是原生的元素对象，这点是需要注意的。




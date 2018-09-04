#### :first-child

##### :first-child选择器是css2中定义的选择器，匹配的是某父元素的第一个子元素

##### 匹配规则是 `el:first-child`:

* 第一步，查找el选择器匹配元素的所有同级元素
* 第二步，在同级元素中查找第一个元素
* 第三步，检验第一个元素是否与选择器el匹配

```html
<div>
  <p>第一个子元素</p>
  <h1>第二个子元素</h1>
  <span>第三个子元素</span>
  <span>第四个子元素</span>
</div>
```
* p:first-child: 匹配到的是p元素，因为p元素是div的第一个子元素
* h1:first-child：匹配不到任何元素，因为h1是div的第二个子元素，而不是第一个
* span:first-child：匹配不到任何元素，因为两个span元素都不是div的第一个子元素
* :first-child：匹配到的是p元素，因为div的第一个元素就是p元素

#### :first-of-type
##### :first-of-type 匹配的是该选择器的第一个元素
```html
<div>
  <p>第一个子元素</p>
  <h1>第二个子元素</h1>
  <span>第三个子元素</span>
  <span>第四个子元素</span>
</div>
```
* p:first-of-type：匹配到的p元素，因为p元素是div中所有为p的子元素中的第一个
* h1:first-of-type：匹配到的是h1元素，因为h1元素是div中所有为h1的子元素中的第一个
* span:first-of-type：匹配到的是第三个子元素span。这里div有两个为span的子元素，匹配到的是第一个
* first——of-type：匹配到的是p元素

##### 同样类型的选择器:last-child 和 :last-of-type、:nth-child(n) 和 :nth-of-type(n)

** 注意**

##### 这段代码，没有像我们期望中的标红.test元素（即第2个段落标签），如果没理解到上面提到的语法关键词意思，第一反应可能会产生“:first-of-type带class写法浏览器不能识别，失效，这是bug”的错误理解。
##### 我们不能简单粗暴，理所当然的将上面的代码错误理解为“匹配父元素.box内第一个.test元素”，我们按上面提到关键词解析下：.box .test:first-of-type
##### 即：匹配父元素.box内同类型标签元素P中的第一个元素.test，但我们看到.test 明显是父元素.box内同类型标签元素P中的第二个元素,所以.test元素（即第2个段落标签）并没有被匹配标红！

要匹配选中.test,我们可以这样改写：
`.box .test:nth-child(3)`
或
`.box .test:nth-of-type(2)`

注：nth-***选择器前面的nth并不是某些单词的英文缩写,正确理解是：n表示不定序数词，可理解成第n个的意思；th表示后缀SUFFIX ，构成序数词表示方式 ，如5th ，可表示日历中的5号，仅此而已。



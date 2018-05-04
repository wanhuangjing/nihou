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





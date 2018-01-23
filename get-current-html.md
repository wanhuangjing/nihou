##### jQuery.html() 是获取当前节点下的html代码，并不包含当前节点本身的代码，然而我们有时候的确需要，可以通过jQuery.prop("outerHTML")的方式设置。

##### 很多jQuery的使用者都对这一问题深感疑惑。为什么在众多方便的各种获取属性和设置属性的方法中就不能像DOM中一样直接设置html元素的outerHTML呢？

##### 因为原生JS DOM里有一个内置属性 outerHTML （看清大小写哦，JS是区分大小写的）用来获取当前节点的html代码(包含当前节点)，所以用jQuery的prop()能拿到

1. jquery获取outerhtml
  ```javascript
  <div class="test"><p>hello，你好！</p></div>
  <script>
    $(".test").prop("outerHTML");
  </script>
  ```

1. jquery设置outerhtml
  ```javascript
  $('.test').prop('outerHTML', '<input>');
  ```

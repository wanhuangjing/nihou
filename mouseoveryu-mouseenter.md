#### mouseover与mouseenter
##### mouseover事件：不论鼠标指针穿过被选元素或其子元素，都会触发mouseover事件
##### mouseenter事件：只有在鼠标指针穿过被选元素时，才会触发mouseenter事件
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <style>
        .over{
            background-color: #66d3ff;
            width:400px;
            float:left;
            padding: 10px 10px;
        }
        .enter{
            background-color: #66d3ff;
            width:400px;
            float:left;
            margin-left:30px;
            padding: 10px 10px;
        }
        h2{
            background-color: #fff;
            padding: 5px 5px;
        }
    </style>
</head>
<body>
<p>mouseover 事件:不论鼠标指针穿过被选元素或其子元素，都会触发 mouseover 事件。</p>
<p>mouseenter 事件:只有在鼠标指针穿过被选元素时，才会触发 mouseenter 事件。</p>
<div class="over">
    <h2>被触发的 Mouseover 事件次数：<span></span></h2>
</div>
<div class="enter">
    <h2>被触发的 Mouseenter 事件次数：<span></span></h2>
</div>
<script>
    var x = 0,y = 0;
    var div1 = document.getElementsByClassName("over")[0];
    div1.addEventListener("mouseover",function(){
        var span = this.getElementsByTagName("span")[0];
        span.innerText = (x +=1);
    },false);

    var div2 = document.getElementsByClassName("enter")[0];
    div2.addEventListener("mouseenter",function(){
        var span = this.getElementsByTagName("span")[0];
        span.innerText = (y +=1);
    },false);
</script>
</body>
</html>
```

#### mouseouter与mouseleave
##### mouseout事件：不论鼠标指针离开被选元素还是任何子元素，都会触发mouseout事件
##### mouseleave事件：只有在鼠标指针离开被选元素时，才会触发mouseleave事件
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <style>
        .over{
            background-color: #66d3ff;
            width:400px;
            float:left;
            padding: 10px 10px;
        }
        .enter{
            background-color: #66d3ff;
            width:400px;
            float:left;
            margin-left:30px;
            padding: 10px 10px;
        }
        h2{
            background-color: #fff;
            padding: 5px 5px;
        }
    </style>
</head>
<body>
<p> mouseout事件：不论鼠标指针离开被选元素还是任何子元素，都会触发 mouseout 事件。</p>
<p> mouseleave事件：只有在鼠标指针离开被选元素时，才会触发 mouseleave 事件。</p>
<div class="over">
    <h2>被触发的 mouseout 事件次数：<span></span></h2>
</div>
<div class="enter">
    <h2>被触发的 mouseleave 事件次数：<span></span></h2>
</div>
<script>
    var x = 0,y = 0;
    var div1 = document.getElementsByClassName("over")[0];
    div1.addEventListener("mouseout",function(){
        var span = this.getElementsByTagName("span")[0];
        span.innerText = (x +=1);
    },false);

    var div2 = document.getElementsByClassName("enter")[0];
    div2.addEventListener("mouseleave",function(){
        var span = this.getElementsByTagName("span")[0];
        span.innerText = (y +=1);
    },false);
</script>
</body>
</html>
```





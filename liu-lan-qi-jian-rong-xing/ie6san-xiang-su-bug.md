#### 问题描述

##### 三像素bug是IE6中一个经典的bug，当浮动元素与非浮动元素相邻时，这个3像素的bug就会出现

#### css代码如下：

```
<html>
<head>
  <style>
    body{
      margin:0px;
      padding:0px;
    }

    #left_box{
       background:#1C86EE;
       float:left;
       height:100px;
       width:100px;
     }

     #right_box{
        background:#76EE00;
        height:100px;
        width:200px;
        /* float:left;   加上浮动便可*/
      }
  </style>
</head>

<body>
  <div id="left_box"></div>
  <div id="right_box"></div>
</body>
</html>
```



各浏览器下兼容情况

#### ie6

![](/assets/18-4-22-1.png)

#### chrome

![](/assets/18-4-22-2.png)

#### firefox

![](/assets/18-4-22-3.png)






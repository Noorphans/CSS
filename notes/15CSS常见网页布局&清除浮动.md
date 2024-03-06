[toc]



## 常见网页布局

### 标准流布局

由一个个`标准流盒子`自上而下按照它默认显示形式而排列，每个元素在水平方向上`独占一行`，并且默认情况下元素的宽度会充满其父容器的宽度。

![image-20240229171816406](http://images.newstar.net.cn/sally-imgsimage-20240229171816406.png) 



\- 举例说明：

```html
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <style>
    * {
      margin: 0;
      padding: 0;
    }

    li {
      list-style: none;
    }

    .top {
      height: 50px;
      background-color: #999;
    }

    .banner {
      width: 980px;
      height: 150px;
      background-color: #999;
      margin: 10px auto;
    }

    .box {
      width: 980px;
      margin: 0 auto;
      height: 300px;
      background-color: pink;
    }

    .box li {
      float: left;
      width: 237px;
      height: 300px;
      background-color: #999;
      margin-right: 10px;
    }

    .box .last {
      margin-right: 0;
    }

    /* 只要是通栏的盒子(和浏览器一样宽) 不需要指定宽度 */
    .footer {
      height: 200px;
      background-color: #999;
      margin-top: 10px;
    }
  </style>
</head>

<body>
  <div class="top">top</div>
  <div class="banner">banner</div>
  <div class="box">
    <ul>
      <li>1</li>
      <li>2</li>
      <li>3</li>
      <li class="last">4</li>
    </ul>
  </div>
  <div class="footer">footer</div>
</body>
```



![image-20240229172000936](http://images.newstar.net.cn/sally-imgsimage-20240229172000936.png)





### 浮动布局注意点

#### 浮动和标准流的父盒子搭配。

`先用标准流的父元素排列上下位置, 之后内部子元素采取浮动排列左右位置`

#### 一个元素浮动了，理论上其余的兄弟元素也要浮动。

* 一个盒子里面有多个子盒子，如果其中一个盒子浮动了，其他兄弟尽量也添加浮动，以防止引起问题。

* `浮动的盒子只会影响浮动盒子后面的标准流,不会影响前面的标准流.`(所以浮动的盒子**总是尽量靠近前面盒子的下边缘**显示)







## 清除浮动

思考：我们前面浮动元素有一个标准流的父元素, 他们有一个共同的特点,都是有高度的. 但是, 所有的父盒子都必须有高度吗? 

理想中的状态, 让子盒子撑开父亲. 有多少孩子,我父盒子就有多高.但是不给父盒子高度会有问题吗?…..



### 为什么需要清除浮动？

1. 因为父级盒子很多情况下，不方便给高度，但是子盒子浮动又不占有位置，最后父级盒子高度为 0 时，就会影响下面的标准流盒子。

2.  `浮动元素不再占用原文档流的位置，所以它会对后面的元素排版产生影响`

![1571555883628](http://images.newstar.net.cn/sally-imgs1571555883628.png)





### 清除浮动本质

* 清除浮动的本质是清除浮动元素造成的影响：浮动的子标签无法撑开父盒子的高度

- 如果父盒子本身有高度，则不需要清除浮动
- `清除浮动之后，父级就会根据浮动的子盒子自动检测高度。父级有了高度，就不会影响下面的标准流了`



### 清除浮动样式

语法：

```css
 选择器{clear:属性值;} 
```

![1571555980419](http://images.newstar.net.cn/sally-imgs1571555980419.png)

> 我们实际工作中， 几乎只用 `clear: both;`

`清除浮动的策略是:  闭合浮动. `(简单理解就是闭合浮动只限制到父元素里面，关到家里闭合起来)





### 清除浮动的多种方式

**1. 额外标签法**也称为隔墙法，是 W3C 推荐的做法。

2. `父级添加 overflow 属性`

3. `父级添加after伪元素`

4. `父级添加双伪元素`





#### 额外标签法(了解)

**`额外标签法`**也称为`隔墙法`，是 W3C 推荐的做法。

`额外标签法`会在浮动元素末尾添加一个空的标签。

```html
例如 <div style="clear:both"></div>，或者其他标签（如<br />等）。
```

* 优点： 通俗易懂，书写方便

* 缺点： 添加许多无意义的标签，结构化较差

> **注意**：`要求这个新的空标签必须是块级元素。`





\- 举例说明：

```html
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <style>
    .box {
      width: 800px;
      border: 1px solid blue;
      margin: 0 auto;
    }

    .damao {
      float: left;
      width: 300px;
      height: 200px;
      background-color: purple;
    }

    .ermao {
      float: left;
      width: 200px;
      height: 200px;
      background-color: pink;
    }

    .footer {
      height: 200px;
      background-color: black;
    }

    /* 清除浮动 */
    .clear {
      clear: both;
    }
  </style>
</head>

<body>
  <div class="box">
    <div class="damao">大毛</div>
    <div class="ermao">二毛</div>
    <div class="ermao">二毛</div>
    <div class="ermao">二毛</div>
    <div class="ermao">二毛</div>

    <div class="clear"></div>
    <!-- 这个新增的盒子要求必须是块级元素不能是行内元素 -->
    <!-- <span class="clear"></span> -->
  </div>
  <div class="footer"></div>
</body>
```



![image-20240229202825198](http://images.newstar.net.cn/sally-imgsimage-20240229202825198.png)



* 总结：

  1. 清除浮动本质是?

     `清除浮动的本质是 清除浮动元素脱离标准流造成的影响`

  2. 清除浮动策略是?

     `闭合浮动.  只让浮动在父盒子内部影响,不影响父盒子外面的其他盒子.`

  3. 额外标签法?

     `隔墙法, 就是在最后一个浮动的子元素后面添加一个额外标签, 添加 清除浮动样式.`

     `实际工作可能会遇到,但是不常用`

     

     

     

#### 父级添加 overflow

可以给父级添加` overflow` 属性，将其属性值设置为 `hidden、 auto 或 scroll` 。

例如：

```css
overflow:hidden | auto | scroll;
```

* 优点：代码简洁

* 缺点：无法显示溢出的部分

> **注意：**`是给父元素添加代码`

​    

\- 举例说明：

```html
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <style>
    .box {
      /* 清除浮动 */
      overflow: hidden;
      width: 800px;
      border: 1px solid blue;
      margin: 0 auto;
    }

    .damao {
      float: left;
      width: 300px;
      height: 200px;
      background-color: plum;
    }

    .ermao {
      float: left;
      width: 200px;
      height: 200px;
      background-color: pink;
    }

    .footer {
      height: 200px;
      background-color: gray;
    }
  </style>
</head>

<body>
  <div class="box">
    <div class="damao">大毛</div>
    <div class="ermao">二毛</div>
  </div>
  <div class="footer"></div>
</body>
```



​     

​		

#### 父级添加伪元素:after (牢记)

> **给父级添加after伪元素**

`:after`方式是额外标签法的升级版。直接复制语法：

```css
 .clearfix:after {  
   content: ""; 
   display: block; 
   height: 0; 
   clear: both; 
   visibility: hidden;  
 } 
 .clearfix {  /* IE6、7 专有 */ 
   *zoom: 1;
 }   
```

优点：没有增加标签，结构更简单

缺点：照顾低版本浏览器

代表网站： 百度、淘宝网、网易等



\- 举例说明：

```html
<style>
    /* 添加伪元素 ，伪元素默认是行内元素，要转为块级元素 */
    .clearfix:after {
      content: "";
      display: block;
      height: 0;
      /* 核心语句 清除 */  
      clear: both;
      visibility: hidden;
    }

    /* CSS为了兼容IE6、7 清除浮动的固定写法 */
    .clearfix {
      *zoom: 1;
    }

    .box {
      width: 800px;
      border: 1px solid blue;
      margin: 0 auto;
    }

    .damao {
      float: left;
      width: 300px;
      height: 200px;
      background-color: purple;
    }

    .ermao {
      float: left;
      width: 200px;
      height: 200px;
      background-color: pink;
    }

    .footer {
      height: 200px;
      background-color: black;
    }
  </style>
</head>

<body>
   <!-- 给父元素添加 -->  
  <div class="box clearfix">
    <div class="damao">大毛</div>
    <div class="ermao">二毛</div>
  </div>
  <div class="footer"></div>
</body>
```

简单理解：伪元素默认是行内元素，要转为块级元素，相当于额外标签隔墙法 在整个盒子最后面添加一个盒子，添加的这个盒子里有clear: both;可以清除浮动， 里面的元素随便怎么浮动，添加的这个盒子已经把他们隔开了。(不需要在末尾单独加标签，但通过CSS生成最后一个标签 帮我们隔开了)







#### 父级添加双伪元素(更推荐使用)

> **给父元素添加双伪元素:before & :after**

直接复制语法：

```css
 .clearfix:before,.clearfix:after {
   content:"";
   display:table; 
 }
 .clearfix:after {
   clear:both;
 }
 .clearfix {
    *zoom:1;
 }   
```

优点：代码更简洁

缺点：照顾低版本浏览器

代表网站：小米、腾讯等



\- 举例说明：

```html
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <style>
    .clearfix:before,
    .clearfix:after {
      content: "";
      display: table;
    }

    .clearfix:after {
      clear: both;
    }

    .clearfix {
      *zoom: 1;
    }

    .box {
      width: 800px;
      border: 1px solid blue;
      margin: 0 auto;
    }

    .damao {
      float: left;
      width: 300px;
      height: 200px;
      background-color: purple;
    }

    .ermao {
      float: left;
      width: 200px;
      height: 200px;
      background-color: pink;
    }

    .footer {
      height: 200px;
      background-color: black;
    }
  </style>
</head>

<body>
    <!-- 给父盒子添加 -->  
  <div class="box clearfix">
    <div class="damao">大毛</div>
    <div class="ermao">二毛</div>
  </div>
  <div class="footer"></div>
</body>
```

简单理解：前后都堵住，完全闭合，里面随便怎么浮动 不会跑





## 清除浮动总结

为什么需要清除浮动？

1. 父级没高度。
2. 子盒子浮动了。
3. 影响下面布局了，我们就应该清除浮动了。

![image-20240301192849170](http://images.newstar.net.cn/sally-imgsimage-20240301192849170.png)


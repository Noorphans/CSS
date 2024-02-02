# CSS元素显示模式

[toc]



了解元素的显示模式可以更好的让我们布局页面. 

1. 什么是元素的显示模式
2. 元素显示模式的分类
3. 元素显示模式的转换



## 什么是元素显示模式

* 目标：能够说出元素有几种显示模式

* 作用：网页的标签非常多，在不同地方会用到不同类型的标签，了解他们的特点**可以更好的布局我们的网页**。
* 元素显示模式就是`元素（标签）以什么方式进行显示`，比如< div>自己占一行，比如一行可以放多个< span>。
* HTML 元素一般分为`块元素`和`行内元素`两种类型。











## 元素显示模式的分类



### 块级元素Block

* 常见的块元素有< h1>~< h6>、< p>、< div>、< ul>、< ol>、< li>、< section>等，其中 `< div>` 标签是最`典型的块元素`。

> **块级元素的特点：**
>
> 1. 比较霸道，`自己独占一行`。
> 2. 高度，宽度、外边距以及内边距都可以控制。(内外边距掌握盒子模型再回看)
> 3. 宽度默认是容器（父级宽度）的100%。(如果不给宽度，那就默认和父级宽度一样)
> 4. 是一个容器及盒子，里面`可以放行内或者块级元素`。(除了**文字类元素**里不能放)



\- 举例说明：

```html
<style>
    div {
      /* div不给宽度 默认父级body宽度 */

      /* width: 200px; */
      height: 200px;
      background-color: plum;
    }
  </style>
</head>

<body>
  <div>div比较霸道，自己独占一行</div>瑟瑟发抖

   <div>
    <p>块级元素可以放块级元素</p>
    <span>也可以放行内元素</span>
  </div>
</body>
```

> **注：**
>
> 1. **`文字类的元素内不能使用块级元素`**
> 2. `< p> `标签主要用于存放文字，因此 < p> 里面`不能放块级元素`，**特别是不能放< div>**
> 3. 同理, `< h1>~< h6>`等都是文字类块级标签，里面也`不能放其他块级元素`







### 行内元素Inline

常见的行内元素有 < a>、< strong>、< b>、< em>、< i>、< del>、< s>、< ins>、< u>、< span>等，其中`< span>` 标签是`最典型的行内元素`。有的地方也将行内元素称为`内联元素`。

>**行内元素的特点：**
>
>1. `相邻行内元素在一行上，一行可以显示多个。`(不会独占一行，就像是一行排列的小物件)。
>2. 高、宽直接设置是无效的。
>3. 默认宽度就是它本身内容的宽度。(也就是你写的有多少字就有多宽)
>4. 行内元素`只能容纳文本文字`或其他`行内元素`。



\- 举例说明：

```html
  <style>
    span {
      /* 高、宽直接设置是无效的。 */
      width: 200px;
      height: 200px;

      background-color: skyblue;
    }
  </style>
</head>

<body>
  <span>sally是个女汉子吗</span> <strong>是个女孩子</strong>
  <span>sally</span> <strong>是个女孩子</strong>
    
  <span>行内元素只能容纳文本文字和其他行内元素<strong>比如strong加粗</strong>and <em>em斜体</em></span>  
</body>
```

> **注：**
>
> 1. 链接里面不能再放链接
> 2. `特殊情况`链接 `< a>` 里面`可以放块级元素`，`但`是给 < a> `转换`一下`块级模式`最安全---->详见第三章节模式转换

\- 举例说明：

< a> 元素内部放置块级元素，同时希望 < a> 元素本身也具有块级元素的特性?

```html
 <!-- 将 <a> 元素的 display 属性设置为 block 或 inline-block  -->
<a href="#" style="display: block;">
    <div>这是一个块级元素</div>
    <p>这也是一个块级元素</p>
</a>
```









### 行内快元素Inline-block

在行内元素中有几个特殊的标签: < img />、< input />、< td>，它们`同时具有块元素和行内元素的特点`。有些资料称它们为`行内块元素`

> **行内块元素的特点：**
>
> 1. 和相邻行内元素（行内块）在一行上，但是他们之间会`有空白缝隙`。一行可以显示多个（**行内元素特点**）。
>    * 简单理解：外观上`表现为行内元素`，但又可以`像块级元素一样设置宽度、高度和内外边距`等。
> 2. 默认宽度就是它本身内容的宽度（行内元素特点）。
> 3. 高度，行高、外边距以及内边距都可以控制（**块级元素特点**）。
> 4. 行内块级元素常用于创建水平方向的导航栏、按钮等，既具有行内元素的水平流排列，又具有块级元素的宽高设置能力。(适用于水平方向的布局)



\- 举例说明:

```html
<style>
    /* 行内元素与块级元素特点并存 */
    input {
      width: 249px;
      height: 34px;
    }
  </style>
</head>

<body>
  <input type="text">
  <input type="text">
</body>
```

![image-20240122195732911](http://images.newstar.net.cn/sally-imgsimage-20240122195732911.png) 







### 元素显示模式总结

![image-20240122195955135](http://images.newstar.net.cn/sally-imgsimage-20240122195955135.png) 

> 学习元素显示模式的**主要目的就是分清它们各自的特点**，当我们网页布局的时候，**在合适的地方用合适的标签元素**









## 元素显示模式的转换

 目标：能够写出元素显示模式的相互 转换代码

* **特殊情况下**，我们需要元素**模式的转换**，简单理解: 一个模式的元素需要另外一种模式的特性
* 比如，想要增加链接 < a> 的触发范围(增加宽高度就有了块级元素特性)
* 三种转换模式：
  1. **`转换为块元素：display:block;`**
  2. 转换为行内元素：display:inline;
  3. **`转换为行内块：display: inline-block;`**



### 转为块元素(重点记)

1. **行内**元素 转换为 **块级**元素

```html
 <style>
    a {
      /* 行内元素a 转为块元素 可设置宽高 */
      display: block;

      text-decoration: none;
      width: 300px;
      height: 100px;
      background-color: paleturquoise;
    }
  </style>
</head>

<body>
  <!-- 将 <a> 元素的 display 属性设置为 block 或 inline-block -->
  <!-- 这样它就会表现为块级元素或行内块级元素，而不再是默认的行内元素。 -->
  <a href="#">行内元素a 转为块级元素 可设置宽高</a>
</body>
```



2. **行内块级**元素 转换为 **块级**元素

```html
  <style>
    /* 行内块级元素 转为 块级元素 独占一行 */
    input {
      width: 300px;
      height: 80px;
      background-color: palegoldenrod;
      display: block;
    }

    td {
      border: 1px solid pink;
      width: 320px;
      height: 100px;
      display: block;
    }
  </style>
</head>

<body>
  <input type="text" placeholder="行内块级元素input 转为块元素独占一行">
  <input type="text" placeholder="行内块级元素input 转为块元素独占一行">


  <table>
    <tr>
      <td>行内块级元素td 转为块元素独占一行</td>
      <td>行内块级元素td 转为块元素独占一行</td>
      <td>行内块级元素td 转为块元素独占一行</td>
    </tr>
  </table>

</body>
```







### 转为行内元素

1. **块级**元素 转换为 **行内**元素

```html
 <style>
    div {
      /* 块级元素div 转为行内元素 */
      display: inline;

      /* 转为行内元素 宽高设置无效 */
      width: 600px;
      height: 200px;

      background-color: red;
    }
  </style>
</head>

<body>
  <div>块级元素转行内元素 宽高设置无效</div>
</body>
```



2. **行内块**级元素 转换为 **行内**元素

```html
  <style>
    td {
      border: 1px solid pink;
      width: 320px;
      height: 100px;
      display: inline;
    }
  </style>
</head>

<body>
  <table>
    <tr>
      <td>行内块级元素td 转为块元素独占一行</td>
      <td>行内块级元素td 转为块元素独占一行</td>
      <td>行内块级元素td 转为块元素独占一行</td>
    </tr>
  </table>
</body>
```







### 转为行内块元素(重点)

1. **行内**元素 转换为 **行内块**级元素

```html
  <style>
    span {
      width: 300px;
      height: 20px;
      background-color: blanchedalmond;

      /*行内元素 转为行内快元素 可设置宽高  display理解为转换*/
      display: inline-block;

    }
  </style>
</head>

<body>
  <span>span行内元素 转为行内块元素 </span>
  <span>在一行 有空隙 宽高可设置</span>
    
</body>
```



2. **块级**元素 转换为 **行内块**级元素

```html
  <style>
    /* 块级 转 行内块元素 */
    h2 {
      width: 300px;
      height: 50px;
      color: brown;
      background-color: palegoldenrod;
      display: inline-block;
    }
  </style>
</head>

<body>
  <h2>块级 转 行内块元素</h2>
  <h2>块级 转 行内块元素</h2>
    
</body>
```

![image-20240123190636970](http://images.newstar.net.cn/sally-imgsimage-20240123190636970.png) 









## 拓展-单行文字垂直居中的代码

* CSS 没有给我们提供文字垂直居中的代码. 这里我们可以使用**一个小技巧**来实现. 
* 解决方案: `让文字的行高等于盒子的高度` 就可以让文字在当前盒子内垂直居中(记住是**单行文字**哦)





### 单行文字垂直居中的原理



* 文字行高 是由文字本身的高度、上空隙和下空隙组成(上下空隙看不见 但存在)

![1570870368253](http://images.newstar.net.cn/sally-imgs1570870368253.png) 



* 比如 盒子本身高度为40，给一个行高设置40的高度(也就是文字本身高度+上下空隙=40)

  ![image-20240131180513422](http://images.newstar.net.cn/sally-imgsimage-20240131180513422.png)



 ![image-20240124095637743](http://images.newstar.net.cn/sally-imgsimage-20240124095637743.png) 

> 简单理解: 行高的`上空隙和下空隙把文字挤到中间`了. 如果行高`小于`盒子高度,`文字会偏上`,如果行高`大于`盒子高度,则`文字偏下`


# CSS选择器

[toc]



## CSS选择器的作用

![image-20240115174942595](http://images.newstar.net.cn/sally-imgsimage-20240115174942595.png) 

* `选择器`(选择符)就是根据不同需求把不同的标签选出来这就是选择器的作用。 简单来说，就是`选择标签用的`。
* 比如：

![image-20240112164406638](http://images.newstar.net.cn/sally-imgsimage-20240112164406638.png) 

以上 CSS 做了两件事：

1. 把所有h1标签选没出来。 选择器（选对人）。

2. 设置这些标签的样式，颜色改为红色，字体设置为25像素（做对事）。





## 选择器分类

**选择器**分为`基础选择器`和`复合选择器`两个大类，复合选择器是建立在基础选择器之上，对基本选择器进行组合形成的。





## 基础选择器

目标：能够使用CSS基础选择器

1. 基础选择器是由`单个选择器`组成的
2. 基础选择器又包括：`标签选择器、类选择器、id 选择器`和`通配符选择器`





### 标签选择器

1. **标签选择器**（元素选择器）**是**指用 **HTML标签名称**作为选择器，按标签名称分类，为页面中某一类标签指定统一的 CSS 样式。
2. 作用：标签选择器可以把某一类标签全部选择出来，比如所有的< div>标签和所有的< span> 标签
   * 优点：能快速为页面中同类型的标签统一设置样式。
   * 缺点：不能设计差异化样式，只能选择全部的当前标签

3. 语法：

```html
标签名 {
	属性1: 属性值1;
	属性2: 属性值2;
	属性3: 属性值3；
	...
}
```

 

\- 举例说明：

```html
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <style>
    p {
      color: blue;
      font-size: 18px;
      font-family: serif;

    }

    div {
      color: orange;
    }
  </style>
</head>

<body>
  <P>男士</P>
  <P>男士</P>
  <!-- div就是盒子 装网页内容 -->
  <div>女士</div>
  <div>女士</div>
</body>
```





#### 类选择器

* 想要**差异化选择**不同的标签，单独选一个或者某几个标签，可以使用**类选择器**
* **口诀:** 样式`点`定义 结构`类(class)`调用 一个或多个 开发最常用
* 语法：

```html
.类名 {
	属性1: 属性值1
	...
}
```



\- 举例说明：

```html
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>基础选择器之类选择器</title>
  <style>
    /* 类选择器口诀: 样式点定义 结构类(class)调用 一个或多个 开发最常用 */
    .blue {
      color: plum;
    }

    .red {
      color: red;
    }
  </style>
</head>

<body>
  <ul>
    <li class="blue">冰雨</li>
    <li class="red">来生缘</li>
    <li>李香兰</li>
    <li class="memeda">生僻字</li>
    <li class="star-sing">江南style</li>
  </ul>
  <div class="red">我也想变红色</div>
</body>
```

> **注：**
>
> 1. 类选择器使用“.”（英文点号）进行标识，后面紧跟类名（**自定义**，我们自己命名的），**不能用标签名作为名字**
> 2. 可以理解为给这个标签起了一个名字，来表示。
> 3. 长名称或词组可以使用**中横线**来为选择器命名。
> 4. **不要使用纯数字、中文等命名，尽量使用英文字母来表示**。
> 5. 命名要有意义，尽量使别人一眼就知道这个类名的目的。
> 6. 命名规范：见附件（ Web 前端开发规范手册.doc）或 https://onestar.love/blog/38





##### 类选择器-多类名

* 各个类名中间用空格隔开，就是给**某个标签添加多个类名**，从而达到更多的选择目的。 
* 这些类名都可以选出这个标签.简单理解就是**一个标签有多个名字**. 
* 这个标签就可以分别具有这些类名的样式,从而节省CSS代码,统一修改也非常方便.
* 类名选择器在后期布局比较复杂的情况下，还是较多使用的

 ![淘宝网多类名](http://images.newstar.net.cn/sally-imgs%E6%B7%98%E5%AE%9D%E7%BD%91%E5%A4%9A%E7%B1%BB%E5%90%8D.png)



###### 多类名使用方式

> (1) 在标签class 属性中写 多个类名
>
> (2) 多个类名中间必须用空格分开
>
> (3) 这个标签就可以分别具有这些类名的样式

```html
  <style>
    .box {
      width: 150px;
      height: 100px;
    }

    .red {
      background-color: red;
    }

    .pink {
      background-color: pink;
    }

    .gray {
      background-color: gray;
    }
  </style>
</head>

<body>
  <div class="box red"></div>
  <div class="box pink"></div>
  <div class="box gray"></div>
</body>
```

![image-20240114130933684](http://images.newstar.net.cn/sally-imgsimage-20240114130933684.png) 





###### 多类名开发中使用场景

(1) 可以把一些标签元素相同的样式(共同的部分)放到一个类里面.**相同样式放在一个类名里，方便统一修改**

(2) 这些标签都可以调用这个公共的类,然后再调用自己独有的类.

(3) 从而节省CSS代码,统一修改也非常方便

```html
<style>
    .pink {
      color: pink;
    }

    .fontWeight {
      font-weight: bold;
    }

    .font40 {
      font-size: 40px;
    }

    .font14 {
      font-size: 14px;
    }
  </style>
</head>

<body>
  <div class="pink fontWeight font40">亚瑟</div>
  <div class="font40">刘备</div>
  <div class="font14 pink">安其拉</div>
  <div class="font14">貂蝉</div>
</body>
```





#### id选择器

* id 选择器可以为标有特定 id 的 HTML 元素指定特定的样式
* HTML 元素以 `id 属性`来设置 id 选择器，CSS 中 id 选择器以“`#`" 来定义。
* 语法：

```html
#id名 {
	属性1: 属性值1;
	...
}
```



\- 举例说明：

```html
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <style>
    /* 这里把 html  body  div  span  li 等等的标签都改为了红色 */
    * {
      color: aqua;
    }
  </style>
</head>

<body>
  <div>这是一个盒子容器</div>
  <span>我的</span>
  <ul>
    <li>这是无序列表</li>
  </ul>
</body>

```

> **注意**：`id 属性只能在每个 HTML 文档中出现一次。口诀: 样式#定义,结构id调用, 只能调用一次, 别人切勿使用`.







#### id选择器和类选择器的区别

1. 类选择器（class）好比人的名字，一个人可以有多个名字，同时一个名字也可以被多个人使用。
2. **id 选择器**好比人的身份证号码，全中国是**唯一**的，**不得重复**。
3. id 选择器和类选择器最大的不同在于使用次数上。
4. 类选择器在修改样式中用的最多，**id 选择器**一般用于页面唯一性的元素上，**经常和 JavaScript 搭配使用**。





#### 通配符选择器

在 CSS 中，通配符选择器使用“`*`”定义，它表示选取页面中所有元素（标签）。

![image-20240115145101377](http://images.newstar.net.cn/sally-imgsimage-20240115145101377.png) 

* 通配符选择器不需要调用， 自动就给所有的元素使用样式
* 特殊情况才使用，后面讲解使用场景
* 比如，清除所有的元素标签的内外边距(后期详解)

![image-20240115143303868](http://images.newstar.net.cn/sally-imgsimage-20240115143303868.png) 







## 基础选择器总结

![基础选择器总结](http://images.newstar.net.cn/sally-imgs%E5%9F%BA%E7%A1%80%E9%80%89%E6%8B%A9%E5%99%A8%E6%80%BB%E7%BB%93.png)

> 每个基础选择器都有使用场景，都需要掌握!  如果是修改样式， 类选择器是使用最多的









## 复合选择器

1. 复合选择器可以更准确、更高效的选择目标元素（标签）
2. 复合选择器是由两个或多个基础选择器，通过不同的方式组合而成的
3. 常用的复合选择器包括：`后代选择器、子选择器、并集选择器、伪类选择器`等等



### 后代选择器(非常重要)

* **后代选择器**又称为**包含选择器**，可以选择父元素里面子元素。其写法就是把外层标签写在前面，内层标签写在后面，中间用空格分隔。当标签发生嵌套时，内层标签就成为外层标签的后代。
* 语法：

![image-20240118205349008](http://images.newstar.net.cn/sally-imgsimage-20240118205349008.png) 

* 解析：`选择元素 1 里面的所有元素2`(后代元素)
* 比如：

```html
 <style>
    /* 我想把ol里的li变为红色 */
    ol li {
      color: red;
    }

    /* 选择 ul 里面所有的 li标签元素 */
    ul li {
      color: pink;
    }
     
    /* 元素2 可以是儿子，也可以是孙子等,只要是元素1 的后代即可 */
    ol li a {
      color: burlywood;
      text-decoration: none;
    }
    
    /* 元素1 和 元素2 可以是任意基础选择器 */
    .nav li a {
      color: yellow;
    }
  </style>
</head>

<body>
  <ol>
    <li>我是ol 的孩子</li>
    <li>我是ol 的孩子</li>
    <li>我是ol 的孩子</li>
    <li><a href="#">我是孙子</a></li>
  </ol>
    
  <ul>
    <li>我是ul 的孩子</li>
    <li>我是ul 的孩子</li>
    <li>我是ul 的孩子</li>
    <li><a href="#">这个a标签不会有变化</a></li>
  </ul>
    
  <ul class="nav">
    <li>我是ul 的孩子</li>
    <li>我是ul 的孩子</li>
    <li>我是ul 的孩子</li>
    <li><a href="#">这个a标签不会有变化</a></li>
    <li><a href="#">这个a标签不会有变化</a></li>
    <li><a href="#">这个a标签不会有变化</a></li>
  </ul>
</body>
```

> **分析：**
>
> 1. 元素1 和 元素2 中间用`空格隔开`
> 2. 元素1 是父级，元素2 是子级，最终选择的是`元素2`
> 3. 元素2 可以是儿子，也可以是孙子等,**只要是元素1 的后代即可(但建议写全)**
> 4. 元素1 和 元素2 可以是任意基础选择器(如标签选择器、id选择器、类选择器都可以)



\- 举例说明：

* 请将下面的**链接文字**修改为红色。

![image-20240122113918772](http://images.newstar.net.cn/sally-imgsimage-20240122113918772.png) 

```html
 <style>
    /* 只要是后代就行 但建议写全 */
    .nav ul li a {
      color: red;
    }
  </style>
```









### 子选择器(重要)

* **子元素选择器（子选择器）**只能选择作为某元素的最近一级子元素。简单理解就是**选亲儿子元素**
* 语法：

![image-20240118205745823](http://images.newstar.net.cn/sally-imgsimage-20240118205745823.png) 

* 解析：`选择元素 1 里面的所有直接后代(子元素) 元素2`。
* 比如：

```html
<style>
   /* 选择 div 里面所有最近一级 a 标签元素 */
    .nav>a {
      color: aqua;
    }
  </style>
</head>

<body>
  <div class="nav">
    <a href="#">我是儿子</a>
    <p>
      <a href="#">我是孙子</a>
    </p>
  </div>
```

> **分析：**
>
> 1. 元素1 和 元素2 中间用 `大于号` 隔开
> 2. 元素1 是父级，元素2 是子级，`最终选择的是元素2`
> 3. 元素2 必须是`亲儿子`，其孙子、重孙之类都不归他管. 你也可以叫他 亲儿子选择器



\- 举例说明：

* 请将下面的**大肘子**文字修改为红色。

 ![image-20240122115033048](http://images.newstar.net.cn/sally-imgsimage-20240122115033048.png)

```html
 <style>
    .hot>a {
      color: red;
    }
  </style>
```









### 并集选择器 (重要）

1. `并集选择器可以选择多组标签, 同时为他们定义相同的样式`。通常用于集体声明.
2. **并集选择器**是各选择器通过`英文逗号（,）连接而成`，任何形式的选择器都可以作为并集选择器的一部分。
3. 语法：

![image-20240122145502490](http://images.newstar.net.cn/sally-imgsimage-20240122145502490.png) 

> **解析：**  上述语法表示`选择元素1 和 元素2`
>
> * 元素1 和 元素2 中间用`逗号隔开`
> * `逗号`可以理解为`和`的意思
> * 并集选择器通常用于集体声明



\- 举例说明：

```html
  <style>
    /* 请将熊大熊二选出来变为红色 */
    /* div,
    span {
      color: red;
    } */

    /* 请将熊大熊二选出来变为紫色 还有 小猪一家改为紫色 */
    div,
    span,
    .pig li {
      color: plum;
    }
  </style>
</head>

<body>
  <div>熊大</div>
  <span>熊二</span>
  <p>光头强</p>
  <ul class="pig">
    <li>小猪佩奇</li>
    <li>光头强</li>
    <li>猪猪</li>
  </ul>
</body>
```

> **注：** 约定的语法规范，并集选择器喜欢竖着写(末尾选择器不需要逗号)







###  伪类选择器

1. 定义：**伪类选择器** 用于向某些选择器添加特殊的效果，比如给链接添加特殊效果，或选择第1个，第n个元素。

2. 因为**伪类选择器很多**，比如有链接伪类、结构伪类等，所以这里以常用的**链接伪类选择器为例**

3. 语法：伪类选择器书写最大的特点是**用冒号（:）表示**，比如 :hover 、 :first-child 

   

    





#### 链接伪类选择器(常用)

链接伪类有四个：

1. a:link	    选择所有未被访问过的链接(没有点击过的链接)
2. a:visited	 选择所有已访问过的链接(点击过的链接)
3. a:hover	   选择鼠标指针位于其上的链接(鼠标经过的那个链接)
4. a:active	  选择活动链接(鼠标正在按下还未弹起鼠标的那个链接)



\- 举例说明：

```html
<style>
    /* 未被访问过的链接 a:link 把没有点击过的链接选出来 */
    a:link {
      color: red;
      text-decoration: none;
    }

    /* a:visited	选择所有已点击过的链接 */
    a:visited {
      color: antiquewhite;
    }

    /* a:hover 选择鼠标经过的那个链接 */
    a:hover {
      color: pink;
    }

    /* a:active	  选择鼠标正在按下还未松开鼠标的链接*/
    a:active {
      color: cornflowerblue;
    }
  </style>
</head>

<body>
  <a href="#">小猪猪</a>
</body>
```







##### 链接伪类选择器注意事项

 > **注：**
 >
 > 1. 为了确保生效，请按照` LVHA` 的**先后顺序声明** :link ----> :visited ----> :hover -----> :active。
 > 2. **记忆法：** **love hate**  或者 lv 包包 hao 
 > 3. 因为 **a 链接**在浏览器中具**有默认样式**，所以我们实际工作中都需要**给a链接单独指定样式**。



\- 举例说明：

```html
  <style>
    /* 以下写法a链接不生效  需要单独指定样式*/
    body {
      color: aquamarine;
    }

    /* 这样单独写样式才生效 */
    a {
      color: skyblue;
    }
  </style>
</head>

<body>
  <a href="#">小猪佩奇</a>
  <a href="http://www.xxxxxxxx.com">未知的网站</a>
</body>
```







##### 链接伪类选择器实际工作开发中的写法

* 实际开发中先给a链接写一个样式，然后再给鼠标经过a:hover写一个样式即可

![image-20240122160342230](http://images.newstar.net.cn/sally-imgsimage-20240122160342230.png) 



\- 举例说明：

```html
 <style>
    /* 这样单独写样式才生效 */
    a {
      color: gray;
      text-decoration: none;
    }

    a:hover {
      color: pink;
    }
  </style>
</head>

<body>
  <a href="#">小猪佩奇</a>
  <a href="http://www.xxxxxxxx.com">未知的网站</a>
</body>
```







####  :focus 伪类选择器

1. **:focus 伪类选择器** 用于选取获得焦点的表单元素。(同Web APIs之Dom事件基础的焦点事件)
2. 焦点就是光标，一般情况 < input> 类表单元素才能获取，因此这个选择器也**主要针对于表单元素**来说。

![image-20240122161254823](http://images.newstar.net.cn/sally-imgsimage-20240122161254823.png) 

解析： 查看input表单是否被选中？有没有光标？ 如果有，就可以更换背景颜色了。也就是*把获得光标的input表单元素选取出来* 









## 复合选择器总结

![1570868930472](http://images.newstar.net.cn/sally-imgs1570868930472.png) 
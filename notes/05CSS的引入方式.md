# CSS的引入方式

[toc]



## CSS的三种样式表

目标：能够说出CSS的三种引入方式

按照 CSS 样式书写的位置（或者引入的方式），CSS 样式表可以分为三大类：

1. 行内样式表（行内式）

2. 内部样式表（嵌入式）

3. 外部样式表（链接式）





### 内部样式表

内部样式表：又称内嵌样式表，是写到html页面内部，是将所有的 CSS 代码抽取出来，单独放到一个 < style> 标签中

```css
<style>
 div {
 color: red;
 font-size: 12px;
 }
</style>
```

解析：

1. < style> 标签理论上可以放在 HTML 文档的任何地方，但一般会放在文档的< ead>标签中
2. 通过此种方式，方便控制当前整个页面中的元素样式设置
3. 代码结构清晰，但是并没有实现结构与样式完全分离(指的是最终CSS样式还是放在在html页面)
4. 使用内部样式表设定 CSS，通常也被称为**嵌入式引入**，这种方式是我们**练习时常用**的方式



\- 举例说明：

```html
  <style>
    div {
      color: pink;
    }
  </style>
</head>

<body>
  <div>所谓内部样式表,就是在html页面内部写样式,但是是单独写到style标签内部.</div>
</body>
```









### 行内样式表

行内样式表：又称**内联样式**表，是`在元素标签内部的style属性中设定 CSS 样式`。适合于修改简单样式

```css
<div style="color: red; font-size: 12px;">青春不常在，抓紧谈恋爱</div>
```

1. style 其实就是标签的属性
2. 在双引号中间，写法要符合 CSS 规范
3. 可以控制当前的标签设置样式
4. 由于书写繁琐，并且没有体现出结构与样式相分离的思想，所以不推荐大量使用，只有对当前元素添加简单样式的时候，可以考虑使用
5. 使用行内样式表设定 CSS，通常也被称为**行内式引入**



\- 举例说明：

![image-20240118180853983](http://images.newstar.net.cn/sally-imgsimage-20240118180853983.png) 









### 外部样式表(常用)

* 实际开发都是**外部样式**表，适合于样式比较多的情况. 核心是:样式单独写到CSS 文件中，之后把CSS文件引入到 HTML 页面中使用.

* 引入外部样式表分为两步：

  1. 新建一个后缀名为 .css 的样式文件，把所有 CSS 代码都放入此文件中。
  2. 在 HTML 页面中，使用< link> 标签引入这个文件。

  ```css
  <link rel="stylesheet" href="css文件路径">
  ```

  \- 举例说明：

  ```html
  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link rel="stylesheet" href="../style.css">
  </head>
  
  <body>
    <div>我的每一滴成功，都如同经过放大镜，进入他们的瞳孔，摄入他们心底。</div>
  </body>
  ```

  

  ![外部样式表](http://images.newstar.net.cn/sally-imgs%E5%A4%96%E9%83%A8%E6%A0%B7%E5%BC%8F%E8%A1%A8.png)

> 使用外部样式表设定 CSS，通常也被称为**外链式**或**链接式引入**，这种方式是开发中常用的方式









## CSS引入方式总结

![css引入方式总结](http://images.newstar.net.cn/sally-imgscss%E5%BC%95%E5%85%A5%E6%96%B9%E5%BC%8F%E6%80%BB%E7%BB%93.png)







## Chrome调试工具

Chrome 浏览器提供了一个非常好用的调试工具，可以用来调试我们的 HTML 结构和 CSS 样式



### 打开调试工具

打开 Chrome 浏览器，按下 **F12键**或者 **右击页面空白处 ——> 检查**

![谷歌调试工具](http://images.newstar.net.cn/sally-imgs%E8%B0%B7%E6%AD%8C%E8%B0%83%E8%AF%95%E5%B7%A5%E5%85%B7.png)







###  使用调试工具

1. **Ctrl+滚轮** 可以放大开发者工具代码大小。
2. 左边是 HTML 元素结构，右边是 CSS 样式。
3. 右边 CSS 样式可以改动数值（左右箭头或者直接输入）和查看颜色。
4. **Ctrl + 0** 复原浏览器大小。
5. 如果点击元素，发现右侧没有样式引入，极有可能是类名或者样式引入错误。
6. 如果有样式，但是样式前面有**黄色叹号提示**，则是样式属性书写错误。

![image-20240118203813557](http://images.newstar.net.cn/sally-imgsimage-20240118203813557.png) 
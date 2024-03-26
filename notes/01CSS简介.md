# CSS入门

[toc]



## CSS使用场景

**CSS** 的主要使用场景就是**美化网页,布局页面**的

1. HTML 的局限性
2. CSS-网页的美容师





### HTML 的局限性

* HTML**只关注内容的语义**。可以做简单的样式，但是带来的是无尽的臃肿和繁琐
* 比如：
  * < h1> 表明这是一个大标题，< p>表明这是一个段落，< img> 表明这儿有一个图片，< a> 表示此处有链接。





### CSS-网页的美容师

目标：能说出什么是CSS

* `CSS` 是`层叠样式表` ( `Cascading Style Sheets` ) 的简称,也会称之为 `CSS 样式表`或`级联样式表`。

* CSS 也是一种标记语言,主要用于设置HTML页面中的`文本内容`（字体、大小、对齐方式等）、`图片的外形`（宽高、边框样式、

  边距等）以及`版面的布局和外观显示样式`。

* **CSS 可以美化 HTML , 让 HTML 更漂亮，让页面布局更简单**

> **总结**：
>
> 1. HTML 主要做结构,显示元素内容.
>
> 2. CSS 美化 HTML ,布局网页.
>
> 3. **CSS 最大价值: 由HTML专注去做 结构呈现，样式 交给CSS，即 结构( HTML ) 与样式( CSS )相分离。**







## CSS语法规范

* 使用 HTML 时，需要遵从一定的规范，CSS 也是如此。要想熟练地使用 CSS 对网页进行修饰，首先需要了解CSS样式规则。
* **CSS 规则由两个主要的部分构成：选择器以及一条或多条声明。**

 ![css属性规则](http://images.newstar.net.cn/sally-imgscss%E5%B1%9E%E6%80%A7%E8%A7%84%E5%88%99.png)

* 分析：
  1. `选择器`是用于指定 CSS 样式的`HTML标签`，花括号内是对该对象设置的具体样式
  2. 属性和属性值以“键值对”的形式出现
  3. 属性是对指定的对象设置的样式属性，例如字体大小、文本颜色等
  4. 属性和属性值之间用英文 **冒号** “`:`”分开
  5. 多个“键值对”之间用英文 **分号** “`;`”进行区分



* 所有的样式，都包含在 < style> 标签内，表示是样式表。< style> 一般写到 < /head> 上方。

```CSS
<head>
 <style>
 h4 {
 color: blue;
 font-size: 100px;
 }
 </style>
</head>
```









## CSS 代码风格

以下代码书写风格不是强制规范,而是符合实际开发书写方式.

1. **样式格式书写**
2. **样式大小写风格**
3. **样式空格风格**





### 样式格式书写

#### 紧凑格式

![image-20240115174114923](http://images.newstar.net.cn/sally-imgsimage-20240115174114923.png)  



#### 展开格式(强烈推荐)

**强烈推荐第二种格式**， 因为更直观。

![image-20240115174202263](http://images.newstar.net.cn/sally-imgsimage-20240115174202263.png) 







### 样式大小风格

#### 小写(强烈推荐)

强烈推荐样式选择器，属性名，属性值关键字**全部使用小写字母**，特殊情况除外。

![image-20240115174239512](http://images.newstar.net.cn/sally-imgsimage-20240115174239512.png) 



#### 大写

![image-20240115174314252](http://images.newstar.net.cn/sally-imgsimage-20240115174314252.png) 





### 样式空格风格

* 选择器（标签）和大括号中间保留空格
* **属性值前**面，**冒号后**面，保留**一个空格**

![image-20240115174350868](http://images.newstar.net.cn/sally-imgsimage-20240115174350868.png) 





## 代码规范

> 1. 类名语义化,尽量精短、明确，必须以字母开头命名，且`全部字母为小写`，单词之间统一使用短划线“`-`”或下划线“`_`” 连接
> 2. `类名嵌套层`次尽量`不超过三层`
> 3. `尽量避免直接使用元素选择器`
> 4. 属性书写顺序
>    布局定位属性：display / position / float / clear / visibility / overflow
>    尺寸属性：width / height / margin / padding / border / background
>    文本属性：color / font / text-decoration / text-align / vertical-align
>    其他属性（CSS3）：content / cursor / border-radius / box-shadow / text-shadow
> 5. `避免使用id选择器`
> 6. `避免使用通配符*和!important`


# 文本属性

[toc]





CSS Text（文本）属性可定义文本的**外观**，比如文本的颜色、对齐文本、装饰文本、文本缩进、行间距等。

目标：能够设置文本样式



## 文本颜色

**color** 属性用于定义文本的颜色

```css
div { 
 color: red;
}
```

\- 举例说明：

```html
 <style>
    div {
      /* color: deepskyblue; */
      /* color: #5fcf9d; */
      color: rgb(255, 0, 255);
    }
  </style>
</head>

<body>
  <div>幸福就是能简单的呼吸，在呼吸停止之前，没有什么不幸的。</div>
</body>
```



![颜色值](http://images.newstar.net.cn/sally-imgs%E9%A2%9C%E8%89%B2%E5%80%BC.png)

> **开发中最常用的是十六进制**







## 对齐文本

**text-align** 属性用于设置元素内文本内容的水平对齐方式

```css
div {
  text-align: center;
}
```

![对齐文本](http://images.newstar.net.cn/sally-imgs%E5%AF%B9%E9%BD%90%E6%96%87%E6%9C%AC.png)



\- 举例说明：

```html
  <style>
    h2 {
      text-align: center;
    }
  </style>
</head>

<body>
  <h2> 木苏里 《判官》</h2>
</body>
```





## 装饰文本

**text-decoration** 属性规定添加到文本的修饰。可以**给文本添加下划线、删除线、上划线等**

```css
div { 
 text-decoration：underline；
}
```

![修饰文本](http://images.newstar.net.cn/sally-imgs%E4%BF%AE%E9%A5%B0%E6%96%87%E6%9C%AC.png)

> **注：** 
>
> * 重点记住如何**添加下划线** ： text-decoration：underline；
>
> * 如何**删除下划线** ：text-decoration: none;
> * 其余了解即可



\- 举例说明：

```html
  <style>
    .underline {
      /* 下划线 */
      text-decoration: underline;
    }

    /* 删除线 */
    .through {
      text-decoration: line-through;
    }

    /* 删除a链接自带的下划线 */
    a {
      text-decoration: none;
    }
  </style>
</head>

<body>
  <p>吾有三愿</p>
  <p class="underline">一愿曲终人未散</p>
  <p class="through">二愿墨香诸事顺</p>
  <p>三愿晋江早倒闭</p>
  <a href="https://onestar.love/" target="_blank">博客</a>
</body>
```

![image-20240116181526674](http://images.newstar.net.cn/sally-imgsimage-20240116181526674.png) 





## 文本缩进

### text-indent

**text-indent** 属性用来指定文本的第一行的缩进，通常是将**段落的首行缩进**。

```css
div { 
 text-indent: 10px;
}
```

通过设置该属性，所有元素的第一行都可以缩进一个给定的长度，甚至**该长度可以是负值**向左缩进。

 

\-举例说明：

```html
 <style>
    p {
      /* 文本第一行首行缩进 */
      /* text-indent: -20px; */
      text-indent: 20px;
    }
  </style>
</head>

<body>
  <p>在这个喧闹的城市,我们背负了太多的包袱，走过了很多路，吃过了很多苦。寂静夜空，对天仰望，尘世间寻找心灵的安慰，我希望这些文字感动了你。</p>
  <p>
    我们经历了一场兵慌马乱的战争，没有硝烟，没有流血，却伤亡惨重。青春是美好的，带给了我们很多的快乐和激情，可是青春又是悲伤的，当有一天青春不在了，我们会拼命的去怀念，听到一首熟悉的老歌，我们会跟着旋律哼唱几句，看到一张发黄的旧照片，我们的心会百感交织，走在曾经熟悉的校园，会想起自己曾经的初恋，曾经被自己深爱的那个她，现在又过得怎样了，心中有太多太多的感触，同时也会问自己，我的青春去哪了?那年匆匆，还是匆匆那年。
  </p>
</body>
```

![image-20240116185526027](http://images.newstar.net.cn/sally-imgsimage-20240116185526027.png) 



### em

* **em**是一个相对单位，就是当前元素（font-size) **1 个文字的大小**, 如果当前元素没有设置大小，则会按照父元素的 1 个文字大小。

```css
p { 
 text-indent: 2em;
}
```

* 缩进当前元素2个字的大小距离 

![image-20240116185723402](http://images.newstar.net.cn/sally-imgsimage-20240116185723402.png) 







## 行间距

**line-height**属性用于设置行间的距离（行高）。可以控制文字行与行之间的距离.

```css
p { 
 line-height: 26px;
}
```

> 使用FScapture工具测量文字行间距：以第一行文字的下沿为起始位置 到 第二行文字的下沿为末端

![image-20240116191741034](http://images.newstar.net.cn/sally-imgsimage-20240116191741034.png) 



\- 举例说明：

```html
 <style>
    div {
      line-height: 26px;
    }

    p {
      line-height: 25px;
    }
  </style>
</head>

<body>
  <div>中国人</div>
  <p>打开北京、上海与广州的地铁地图，你会看见三张纵横交错的线路网络，这代表了中国最成熟的三套城市轨道交通系统。</p>

  <p> 可即使这样，在北上广生活的人依然少不了对地铁的抱怨，其中谈及最多的问题便是拥挤——对很多人而言，每次挤地铁的过程，都像是一场硬仗。更何况，还都是败仗居多。</p>

  <p> 那么，当越来越多的二线甚至三线城市迎接来了自己的地铁，中国哪里的地铁是最拥挤的呢？</p>
</body>

```

![image-20240116192616372](http://images.newstar.net.cn/sally-imgsimage-20240116192616372.png) 



## 文本属性总结

![文本属性总结](http://images.newstar.net.cn/sally-imgs%E6%96%87%E6%9C%AC%E5%B1%9E%E6%80%A7%E6%80%BB%E7%BB%93.png)





## 扩展补充-white-space

`white-space` 属性用于控制元素内文本的空白处理方式。它有几个常用的取值，包括：

1. **normal**：默认值。连续的空白字符会被合并并且换行符会被处理成空格。文本会根据容器的宽度自动换行。
2. **nowrap**：空白字符不会被合并，`文本不会换行，会在一行上显示`，超出容器的部分会被截断。
3. **pre**：保留空白字符，文本内的空白字符会被保留，换行符会产生换行。这个值通常用于保持代码块等文本的格式。
4. **pre-wrap**：保留空白字符，但是会根据容器的宽度进行换行。即使没有换行符，文本也会根据容器的宽度进行换行。
5. **pre-line**：合并空白字符，但是保留换行符，同时根据容器的宽度进行换行。
6. **inherit**：继承父元素的 `white-space` 属性的值。


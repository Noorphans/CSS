# CSS字体属性

[toc]





CSS Fonts (字体)属性用于定义**字体系列**、大小、粗细、和文字样式（如斜体）

目标：能够设置字体样式

## 字体系列

* CSS 使用`font-family`属性定义文本的字体系列。

![image-20240115183614703](http://images.newstar.net.cn/sally-imgsimage-20240115183614703.png) 

\- 举例说明：

```html
  <style>
    h2 {
      font-family: 'Microsoft YaHei';
    }

    p {
      font-family: 'Times New Roman';
    }

    div {
      font-family: '仿宋';
    }
  </style>
</head>

<body>
  <h2>为段落设置字体</h2>
  <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Quae laudantium autem, animi deserunt quod incidunt porro
    voluptates? Dignissimos animi saepe fugit! Dolor blanditiis dolores ipsa, assumenda eaque provident. Quis, velit.
  </p>
  <div>老鼠爱大米</div>
</body>
```

> * **各种字体之间**必须使用英文状态下的**逗号隔开**
> * 一般情况下,如果有空格隔开的**多个单词组成的字体,加引号**.
> * 尽量使用系统默认自带字体，保证在任何用户的浏览器中都能正确显示
> * 最常见的几个字体：：body {font-family: 'Microsoft YaHei',tahoma,arial,'Hiragino Sans GB';}
> * 多个字体按照前后顺序类推显示，前面字体有就显示前面字体，没有就找下一个









## 字体大小

CSS 使用 `font-size` 属性定义字体大小

```html
 p {  
    font-size: 20px; 
}
```

> 1. px（像素）大小是我们网页的最常用的单位,**字体大小一定要跟单位**
> 2. 谷歌浏览器默认的文字大小为16px
> 3. 不同浏览器可能默认显示的字号大小不一致，我们尽量给一个明确值大小，不要默认大小
> 4. 可以给 body 指定整个页面文字的大小
> 5. **标题标签比较特殊，需要单独指定文字大小**



\- 举例说明：

```html
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <style>
    body {
      font-size: 20px;
    }
 /* 标题标签比较特殊，需要单独指定文字大小 */
    h2 {
      font-size: 16px;
    }
  </style>
</head>

<body>
  <h2>字体大小</h2>
  <P>1.px（像素）大小是我们网页的最常用的单位</P>
  <p>2.谷歌浏览器默认的文字大小为16px</p>
  <p>3.不同浏览器可能默认显示的字号大小不一致，我们尽量给一个明确值大小，不要默认大小</p>
  <p>4.可以给 body 指定整个页面文字的大小</p>
</body>
```

![image-20240116143600095](http://images.newstar.net.cn/sally-imgsimage-20240116143600095.png) 







## 字体粗细

* CSS 使用 `font-weight` 属性设置文本字体的粗细。

```html
p { 
 font-weight: bold;
}
```

![image-20240116142002943](http://images.newstar.net.cn/sally-imgsimage-20240116142002943.png)

* 学会 **把加粗标签（比如 标题标签h 和 strong 等) 变细不加粗**；或者把其他标签加粗
* 比如：

```html
<style>
    .bold {
      /* font-weight: bold; */
      /* 700 后面不要跟单位  等价于 bold 都是加粗的效果 */
      /* 实际开发中,我们跟提倡使用数字 表示加粗或者变细 */
      font-weight: 700;
    }

    h2 {
      /* font-weight: normal; */
      font-weight: 400;
    }

    .normal {
      font-weight: 400;
    }
  </style>
</head>

<body>
  <h2>字体大小</h2>
  <strong>
    <P class="normal">1.px（像素）大小是我们网页的最常用的单位</P>
  </strong>
  <p>2.谷歌浏览器默认的文字大小为16px</p>
  <p class="bold">3.不同浏览器可能默认显示的字号大小不一致，我们尽量给一个明确值大小，不要默认大小</p>
  <p>4.可以给 body 指定整个页面文字的大小</p>

</body> 
```

> **注：** 实际开发中,我们跟**提倡使用数字 表示加粗或者变细** 

![image-20240116143813117](http://images.newstar.net.cn/sally-imgsimage-20240116143813117.png) 





## 文字样式(风格)

CSS 使用 `font-style` 属性设置文本的风格

```html
p {
 /*标准字体样式*/
 font-style: normal;
}
```

![文字倾斜](http://images.newstar.net.cn/sally-imgs%E6%96%87%E5%AD%97%E5%80%BE%E6%96%9C.png) 

> **注意：** 平时我们很少给文字加斜体，**反而要给斜体标签（em，i）改为不倾斜字体** 

\- 举例说明：

```html
  <style>
    p {
      font-style: italic;
    }
  /* 把倾斜变成不倾斜 */
    em {
      font-style: normal;
    }
  </style>
</head>

<body>
  <p>朋友，远在外地找工作的你</p>
  <em>原来不知不觉间，熊出没已经陪伴我们十年了</em>
</body>
```

![image-20240116145846284](http://images.newstar.net.cn/sally-imgsimage-20240116145846284.png) 





## 字体复合属性

字体复合属性可以把以上**文字样式综合来写**, 这样可以更节约代码:

```html
body { 
 font: font-style font-weight font-size/line-height font-family;
}
```

> **注：**
>
> * 使用 font 属性时，**必须按**上面语**法格**式中的**顺序书写**，`不能更换顺序`，并且**各个属性**间以`空格`隔开
> * **不需要设置的属性可以省略**（取默认值），但`必须保留 font-size 和 font-family`属性，**否则 font 属性将不起作用**



\- 举例说明：想要div文字变倾斜 加粗 字号设置为16像素 并且 是微软雅黑

```html
<style>
    /* 想要div文字变倾斜 加粗 字号设置为16像素 并且 是微软雅黑 */
    div {
      /* font-style: italic;
        font-weight: 700;
        font-size: 16px;
        font-family: 'Microsoft YaHei';   
      */

      /* 复合属性: 简写的方式  节约代码 */
      /* font: font-style  font-weight  font-size/line-height  font-family; */
      /* font: italic 700 16px 'Microsoft YaHei'; */
      font: 20px '黑体';
    }
  </style>
</head>

<body>
  <div>三生三世十里桃花,一心一意百行代码</div>
</body>
```









## 字体属性总结

![字体总结](http://images.newstar.net.cn/sally-imgs%E5%AD%97%E4%BD%93%E6%80%BB%E7%BB%93.png)

* 字体复合属性如何写? 里面有什么注意细节?

  1. 按照语法顺序写： style样式、weight粗细、size/line-height字号/行高、family字体
  2. 注意细节：属性间空格隔开，不能更改顺序，字号字体必须保留同时出现

  

* 如果让加粗的文字不加粗显示, 如何让倾斜的文字不倾斜显示?

  1. font-weight: 400;
  2. font-style: normal;


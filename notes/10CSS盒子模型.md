# 盒子模型

[toc]





> **页面布局**要学习**三大核心**, **盒子模型, 浮动 和 定位**.学习好盒子模型能非常好的帮助我们布局页面



## 看透网页布局的本质

> **网页布局的核心本质**： 就是**利用 CSS 摆盒子。**

![1571492334739](http://images.newstar.net.cn/sally-imgs1571492334739.png)

网页布局过程：

1. 先准备好相关的网页元素，网页元素基本都是盒子 Box 。
2. 利用 CSS 设置好盒子样式，然后摆放到相应位置。(最麻烦)
3. 往盒子里面装内容







##  盒子模型(Box Model)组成

* 目标：能够准确阐述盒子模型4个组成部分
* `盒子模型`：就是把`HTML页面中`的`布局元素看作`是一个矩形盒子，**一个标签就是一个矩形盒子**，也就`是一个盛装内容的容器`。

> `CSS 盒子模型本质上是一个盒子`，`封装`周围的 `HTML元素`，它包括：**边框**、**外边距**、**内边距**、和 **实际内容**

* 记忆口诀：

  盒子模型，四方位，边框、内容、内边距加上一个外边距。BCPM(Border、Content、Padding和Margin)

  border是边框；content是内容；padding内边距很重要，边框与内容的距离主要就靠它；margin外边距，他是干啥的？ 盒子与盒子的距离就靠它说话

![image-20240131141931882](http://images.newstar.net.cn/sally-imgsimage-20240131141931882.png) 



![1571492529986](http://images.newstar.net.cn/sally-imgs1571492529986.png)







### 边框(border)

* 目标：能够利用复合写法给元素添加边框，能够计算盒子的实际大小

* border可以设置元素的边框。**边框有三部分**组成:边框**宽度(粗细)** 边框**样式** 边框**颜色**
* 语法：

```css
 border : border-width || border-style || border-color;   
```



![image-20240131142257536](http://images.newstar.net.cn/sally-imgsimage-20240131142257536.png) 



![image-20240131144321832](http://images.newstar.net.cn/sally-imgsimage-20240131144321832.png)

* 边框样式 border-style 可以设置如下值：
  1. none：没有边框即忽略所有边框的宽度（默认值）
  2. `solid`：边框为`单实线`(最为`常用`的)
  3. dashed：边框为虚线  
  4. dotted：边框为点线



\- 举例说明：

```html
<style>
    div {
      width: 300px;
      height: 200px;

      /* 边框的粗细  一般情况下都用 px */
      border-width: 5px;

      /* 边框的样式  solid 实线边框*/
      /* border-style: solid; */

      /* dashed 虚线边框 */
      border-style: dashed;

      /* dotted 点线边框 */
      /* border-style: dotted; */

      /* 边框颜色 */
      border-color: pink;

    }
  </style>
</head>

<body>
  <div></div>
</body>
```



![image-20240131151539955](http://images.newstar.net.cn/sally-imgsimage-20240131151539955.png) 



#### 边框简写和分写

1. 边框简写：

```css
 border: 1px solid red;  
```

> 没有顺序,但建议按照这样的顺序写



2. 边框分开写法：

```css
border-top: 1px solid red; /* 只设定上边框， 其余同理 */
```

>  只设定上边框， 其余同理



\- 举例说明：

```html
 <style>
    div {
      width: 300px;
      height: 200px;
      /* 分写 设置上边框为红色 */
      border-top: 5px solid red;
      border-bottom: 5px solid blue;
      border-left: 5px solid blue;
      border-right: 5px solid blue;

    }
  </style>
</head>

<body>
  <div></div>
</body>
```



> 请给一个 200*200 的盒子，设置上边框为红色，其余边框为蓝色（提示：一定注意边框的层叠性）

```html
 <style>
    div {
      width: 300px;
      height: 200px;
        
     /* border包含四条边 */
      border: 5px solid blue;

      /* 层叠性 只是层叠了 上边框*/
      border-top: 5px solid red;
    }
  </style>
</head>

<body>
  <div></div>
</body>
```





#### 表格的细线边框

1. `border-collapse`属性控制浏览器绘制表格边框的方式。它控制相邻单元格的边框。
2. 语法：

```css
border-collapse:collapse; 
```

解析：collapse 是合并的意思。border-collapse: collapse; 表示**相邻边框合并**在一起



\- 举例说明：

```html
 <style>
    table {
      width: 500px;
      height: 249px;
    }
     
     th {
      height: 40px;
    } 

    table,
    td,
    th {

      /* thead部分细 tbody部分粗 */
      border: 1px solid plum;

      /* 合并相邻的边框  把边框统一变细*/
      border-collapse: collapse;
      font-size: 18px;
      text-align: center;
    }
  </style>
</head>

<body>
  <table align="center" cellpadding="5" cellspacing="0">
    <thead>
      <tr>
        <th>排名</th>
        <th>关键词</th>
        <th>趋势</th>
        <th>今日搜索</th>
        <th>最近七日</th>
        <th>相关链接</th>
      </tr>
    </thead>

    <tbody>
      <tr>
        <td>1</td>
        <td>鬼吹灯</td>
        <td><img src="../images/up.jpg" /></td>
        <td>345</td>
        <td>123</td>
        <td><a href="#">贴吧</a> <a href="#">图片</a> <a href="#">百科</a></td>
      </tr>
      <tr>
        <td>2</td>
        <td>盗墓笔记</td>
        <td><img src="../images/down.jpg" /></td>
        <td>124</td>
        <td>675432</td>
        <td><a href="#">贴吧</a> <a href="#">图片</a> <a href="#">百科</a></td>
      </tr>
      <tr>
        <td>3</td>
        <td>西游记</td>
        <td><img src="../images/up.jpg" /></td>
        <td>212</td>
        <td>7654</td>
        <td><a href="#">贴吧</a> <a href="#">图片</a> <a href="#">百科</a></td>
      </tr>
    </tbody>
  </table>
</body>
```



![image-20240131164117245](http://images.newstar.net.cn/sally-imgsimage-20240131164117245.png)



#### 边框会影响盒子实际大小

边框会额外增加盒子的实际大小 也就是盒子的**边框部分**会**增加盒子总尺寸**。因此我们有**两种方案解决**：

- `测量盒子大小时,不量边框`(测量边框里面)。

- 如果`测量时包含边框`,则需要 `width/height 减去边框宽度`

  比如：盒子宽高是200px，border是10px，测量时不小心把边框一起测量了，这时需手动更改宽高为180px

  ```html
  <style>
      /* 我们需要一个200*200的盒子, 但是这个盒子有10像素的红色边框 */
      /* 算上左右边框  实际大小为220px*220px = 200px + 10px + 10px*/
       div {
        /* width: 200px;
        height: 200px; */
        width: 180px;
        height: 180px;
        background-color: pink;
        border: 10px solid red;
      }
    </style>
  </head>
  
  <body>
    <div></div>
  </body>
  ```

  > **边框分左右，减的时候要减双倍；如果只有右边框，只减一份即可**







### 内边距(padding)

* 目标：能够计算盒子的实际大小

* padding 属性用于设置内边距，即`边框与内容之间的距离`。



#### 内边距简写和分写

1. 分写属性

![1571493260536](http://images.newstar.net.cn/sally-imgs1571493260536.png) 

 ```html
 <style>
    div {
      width: 200px;
      height: 200px;
      background-color: skyblue;
      padding-left: 20px;
      padding-right: 20px;
      padding-top: 20px;
      padding-bottom: 20px;

    }
  </style>
</head>

<body>
  <div> 盒子内容是content盒子内容是content盒子内容是content盒子内容是content</div>
</body>
 ```

![image-20240131175416101](http://images.newstar.net.cn/sally-imgsimage-20240131175416101.png)





2. 简写属性

![image-20240131175754590](http://images.newstar.net.cn/sally-imgsimage-20240131175754590.png)

以上 4 种情况，我们实际开发都会遇到

> 口诀：四边一样则一个，两两相等则两个，两边不同则三个，四边不同记顺时
>
> * 一值代表 上下左右
> * 两值代表上下 和 左右
> * 3值代表上 左右 和 下 
> * 4值代表上 右 下 左 (顺时针)



\- 举例说明：

```html
<style>
    div {
      width: 200px;
      height: 200px;
      background-color: skyblue;

      /* 分写太麻烦 */
      /* padding-left: 20px;
      padding-right: 20px;
      padding-top: 20px; */


      /* 简写 */
      /* 四边一样则一个 都是5px */
      padding: 5px;

      /* 两两相等则两个 上下是5px 左右10px */
      padding: 5px 10px;


      /* 上5px 左右10px 下20px */
      padding: 5px 10px 20px;

      /* 上5px 右10 下20 左30 */
      padding: 5px 10px 20px 30px;

    }
  </style>
</head>

<body>
  <div> 盒子内容是content盒子内容是content盒子内容是content盒子内容是content</div>
</body>
```

![image-20240201195129818](http://images.newstar.net.cn/sally-imgsimage-20240201195129818.png)





#### 内边距会影响盒子实际大小

* 当我们给盒子指定 padding 值之后，发生了 2 件事情：

  1. 内容和边框有了距离，添加了内边距。
  2. padding影响了盒子实际大小。

* 内边距对盒子大小的影响：

  1. 如果盒子已经`有宽度和高度`，此时`再指定内边框`，`会撑大`盒子。
  2. 如何盒子本身`未指定width/height`属性, 则此时`padding不会撑开盒子大小`。
  
* **解决方案：**

  如果保证盒子跟效果图大小保持一致，则让**` width/height 减去多出来的内边距大小`**即可。

```html
 <style>
    div {
      /* 加20内边距变成240*240 */
      /* width: 200px;
      height: 200px; */

      /* 宽高减去内边距两边 */
      width: 160px;
      height: 160px;
      background-color: pink;
      padding: 20px;
    }
  </style>
</head>

<body>
  <div>
    padding会影响盒子实际大小padding会影响盒子实际大小padding会影响盒子实际大小padding会影响盒子实际大小
  </div>
</body>
```



​                            ![image-20240201200346592](http://images.newstar.net.cn/sally-imgsimage-20240201200346592.png)

> **边距也分左右，减的时候要减双倍；如果只有右边距，只减一份即可**









### 外边距(margin)

margin 属性用于设置外边距，即控制盒子和盒子之间的距离。





#### 外边距简写和分写

1. 分写属性

![image-20240201210528405](http://images.newstar.net.cn/sally-imgsimage-20240201210528405.png) 



\- 举例说明：

```html
  <style>
    div {
      width: 200px;
      height: 200px;
      background-color: pink;
    }

    /* 第一个盒子 就给底部设置外边距  */
    /* .one {
      margin-bottom: 20px;
    } */

    /* 第二个盒子 就顶部设置外边距 */
    .two {
      margin-top: 20px;
    }
  </style>
</head>

<body>
  <div class="one">1</div>
  <div class="two">2</div>
</body>
```



2.简写属性

| 值的个数                   | 表达意思                                                     |
| -------------------------- | ------------------------------------------------------------ |
| margin:5px;                | 1个值，代表上下左右都有5像素;                                |
| margin:5px 10px;           | 2个值，代表上下外边距是5像素 左右外边距是10像素；            |
| margin:5px 10px 20px;      | 3个值，代表上外边距是5像素 左右外边距是10像素 下外边距是20像素； |
| margin:5px 10px 20px 30px; | 4个值，代表上是5像素 右是10像素 下是20像素 左是30像素 顺时针 |



> 口诀：四边一样则一个，两两相等则两个，两边不同则三个，四边不同记顺时
>
> * 一值代表 上下左右
> * 两值代表上下 和 左右
> * 3值代表上 左右 和 下 
> * 4值代表上 右 下 左 (顺时针)

```html
 <style>
    div {
      width: 200px;
      height: 200px;
      background-color: pink;
    }

    /* 第二个盒子 就顶部设置外边距 */
    .two {
      /* margin-top: 20px; */

      /* 上下左右都是10像素 */
      margin: 10px;


      /* 上下10px和左右5px */
      margin: 10px 5px;

      /* 上5px 左右10px 下20 */
      margin: 5px 10px 20px;

      /* 上5 右10 下20 左30 */
      margin: 5px 10px 20px 30px;
    }
  </style>
</head>

<body>
  <div class="one">1</div>
  <div class="two">2</div>
</body>
```



![image-20240202131018721](http://images.newstar.net.cn/sally-imgsimage-20240202131018721.png)







#### 外边距典型应用

##### 块级元素水平居中

* 外边距可以`让块级盒子水平居中`的两个条件：

  1. 盒子`必须指定了宽度`（width）。 
  2. 盒子`左右的外边距`都设置为 auto(自动的意思) 。

  ![image-20240202134908563](http://images.newstar.net.cn/sally-imgsimage-20240202134908563.png) 

  

* 常见的写法，以下三种都可以：

  1. margin-left: auto;  margin-right: auto; (只要保证左右auto就可实现居中对齐)
  2. margin: auto; (上下左右都auto)
  3. `margin: 0 auto;`(上下为0 左右auto)---->常用

  > **注意**：**以上方法是让块级元素水平居中**



\- 举例说明：

```html
 <style>
    .header {
      width: 900px;
      height: 200px;
      background-color: pink;
      /* 上下为0 左右auto */
      /* margin: 0 auto; */

      /* 上下为100px 左右auto */
      margin: 100px auto;
    }
  </style>
</head>

<body>
  <div class="header"></div>
</body>
```



![image-20240202151918248](http://images.newstar.net.cn/sally-imgsimage-20240202151918248.png)







##### 行内元素&行内块元素水平居中

> **注：** `行内元素或行内块元素 水平居中 给其父元素添加 text-align:center即可`。

```html
<style>
    .header {
      width: 900px;
      height: 200px;
      background-color: pink;
      margin: 100px auto;

      /* 行内元素或者行内块元素水平居中给其父元素添加 text-align:center 即可 */
      text-align: center;
      font-size: 24px;
      /* 单行内容水平居中 高度和行高一致 */
      line-height: 200px;
    }

    .header img {
      width: 50px;
    }
  </style>
</head>

<body>
  <div class="header">
    <span>里面的文字</span>
  </div>
  <div class="header">
    <img src="../images/down.jpg" alt="">
  </div>
</body>
```



![image-20240202153948293](http://images.newstar.net.cn/sally-imgsimage-20240202153948293.png)





#### 外边距合并

* 使用 `margin` 定义块元素的`垂直外边距`时，可能会出现外边距的合并。

* 主要有两种情况:
  1. **相邻块元素垂直外边距的合并**
  2. **嵌套块元素垂直外边距的塌陷**
  
  >**注意：** **`浮动的盒子不会有外边距合并的问题`**



##### 相邻块元素垂直外边距的合并

* 当上下相邻的两个块元素（兄弟关系）相遇时:

  * 如果`上`面的元素`有`下外边距 `margin-bottom`，`下`面的元素`有`上外边距`margin-top` ,则他们之间的`垂直间距`**不是 margin-bottom 与 margin-top 之和**。而是`取两个值中的较大者`这种现象被称为 **`相邻块元素垂直外边距的合并`**。
  * 也就是说它们的`外边距值会合并为那个较大的值`，所以尽量一个margin值就可以了

  

>**解决方案**：尽量只给一个盒子添加 margin 值。

![image-20240202155637312](http://images.newstar.net.cn/sally-imgsimage-20240202155637312.png) 

```html
 <style>
    .one,
    .two {
      width: 200px;
      height: 200px;
      background-color: pink;
    }

    /* 最后外边距只显示大的 50px */
    .one {
      margin-bottom: 50px;
    }

    .two {
      margin-top: 10px;
    }
  </style>
</head>

<body>
  <div class="one">大毛</div>
  <div class="two">二毛</div>
</body>
```



![image-20240202172801229](http://images.newstar.net.cn/sally-imgsimage-20240202172801229.png)







##### 嵌套块元素垂直外边距的塌陷

* 对于两个`嵌套关系（父子关系）的块元素`，`父元素和子元素`同时`都有上外边距时`：

  * 此时父元素会`塌陷较大的外边距值`。也就是说取其中较大的值合并塌陷。

  * 比如，父上外边距为20px，子上外边距为30px，最终父上外边距会被塌陷为30px，而不是简单地相加得到50px



![image-20240202160858064](http://images.newstar.net.cn/sally-imgsimage-20240202160858064.png)



\- 举例说明：父子元素都有上外边距时，谁的大 就塌陷谁的外边距

```html
 <style>
    .father {
      width: 400px;
      height: 400px;
      background-color: purple;
      /* 顶部外边距50 */
      margin-top: 50px;

    }

    .son {
      width: 200px;
      height: 200px;
      background-color: pink;
      margin-top: 100px;
    }
  </style>
</head>

<body>
  <div class="father">
    <div class="son"></div>
  </div>
</body>
```



![image-20240202162946820](http://images.newstar.net.cn/sally-imgsimage-20240202162946820.png)



> **解决方案：**
>
> 1. 可以为`父元素定义上边框 border`。
> 2. 可以为`父元素定义上内边距 padding`。
> 3. 可以为`父元素添加 overflow:hidden`。(超出部分隐藏裁剪掉)



\- 距离说明：

```html
<style>
    .father {
      width: 400px;
      height: 400px;
      background-color: purple;
      /* 顶部外边距50 */
      margin-top: 50px;

      /* 解决塌陷  */
      /* 1. 边框有色边框线 不美观 改为透明色 */
      /* border: 1px solid transparent; */

      /* 2.上内边距 */
      /* padding-top: 1px; */

      /* 3.把溢出超出部分设置为隐藏 不会使盒子变大*/
      overflow: hidden
    }

    .son {
      width: 200px;
      height: 200px;
      background-color: pink;
      margin-top: 100px;
    }
  </style>
</head>

<body>
  <div class="father">
    <div class="son"></div>
  </div>
</body>
```



![image-20240202165042841](http://images.newstar.net.cn/sally-imgsimage-20240202165042841.png)





#### 扩展知识-BFC块级格式化上下文

1. 添加 `overflow: hidden;` 是一种常见的解决外边距塌陷问题的方法之一。
2. 这是因为当元素的 overflow 属性被设置为除了 visible 以外的值时（如 hidden、auto 或 scroll），会创建一个新的 BFC（块级格式化上下文），`阻止`父元素的上外边距与子元素的上外边距`合并`，从而`解决`了外边距`塌陷`的问题。
3. BFC(Block Formatting Context)是一个独立的渲染区域，其中的元素布局不受外部影响，并且不会影响到外部元素。当一个元素成为 BFC 时，它的外边距不会与其父元素或子元素的外边距合并。

> **注：** 这种方法可能会影响到布局和内容的显示，因此在使用时需要谨慎。



* 通常情况下，可以通过以下方式创建 BFC：
  1. 设置元素的 `float` 属性为除 `none` 以外的值。(left right)
  2. 设置元素的 `position` 属性为 `absolute` 或 `fixed`。
  3. 设置元素的 `display` 属性为 `inline-block`、`flex`、`grid` 或 `table-cell`。
  4. 设置元素的 `overflow` 属性为除 `visible` 以外的值。



* `float` 属性值：
  1. `none`：默认值，元素不浮动，按照正常文档流进行布局。
  2. `left`：元素向左浮动，其他内容会围绕在它的右侧。
  3. `right`：元素向右浮动，其他内容会围绕在它的左侧



* `position` 属性值：
  1. `static`: 默认值，元素遵循正常的文档流。
  2. `relative`: 相对定位，元素的位置相对于它自身在正常文档流中的位置进行偏移。
  3. `absolute`: 绝对定位，元素的位置相对于其最近的非 static 祖先元素进行定位。
  4. `fixed`: 固定定位，元素的位置相对于浏览器窗口进行定位，即使页面滚动也不会改变其位置。



*  `display` 属性值除了显示模式以外还有：
  1. `none`：将元素隐藏，不会在页面上显示。
  2. `flex`：将元素显示为弹性盒子（flex container），可以使用弹性布局来排列其子元素。
  3. `grid`：将元素显示为网格容器（grid container），可以使用网格布局来排列其子元素。
  4. `table`：将元素显示为表格元素，可以用于创建表格布局。
  5. `list-item`：将元素显示为列表项（如 `<li>` 元素）。
  6. `inherit`：继承父元素的 `display` 属性。
  7. `initial`：将元素的 `display` 属性重置为默认值。



* `overflow` 属性值：
  1. `visible`：默认值，内容会溢出到元素框之外。
  2. `hidden`：溢出的内容会被裁剪，不会显示在元素框外面。
  3. `scroll`：如果内容溢出，会显示滚动条以便查看超出的内容。
  4. `auto`：如果内容溢出，会根据需要显示滚动条。







#### 清除内外边距

* `网页元素很多都带有默认的内外边距`，而且不同浏览器默认的也不一致。



![image-20240202173437854](http://images.newstar.net.cn/sally-imgsimage-20240202173437854.png)



* 因此我们在布局前，首先`要清除`下网页元素的`内外边距`。

```css
 * {
    padding:0;   /* 清除内边距 */
    margin:0;    /* 清除外边距 */
  }
```



\- 举例说明：

```html
 <style>
    /* 这句话也是我们css 的第一行代码 */
    * {
      margin: 0;
      padding: 0;
    }

    body {
      background-color: #999;
    }
  </style>
</head>

<body>
  123
  <ul>
    <li>abcd</li>
  </ul>
  <span>行内元素尽量只设置左右的内外边距</span>
</body>
```



![image-20240202194931323](http://images.newstar.net.cn/sally-imgsimage-20240202194931323.png)





> **`注意：`**`行内元素为了照顾兼容性，尽量只设置左右内外边距，不要设置上下内外边距。但转换为块级和行内块元素就可以了`

```html
 <style>
    /* 这句话也是我们css 的第一行代码 */
    * {
      margin: 0;
      padding: 0;
    }

    body {
      background-color: #999;
    }


    span {
      background-color: pink;
      /* margin: 20px; */

      /* 行内元素尽量不设置上下内外边距  因为不起效果 意义不大*/
      margin: 0px 20px;
    }
  </style>
</head>

<body>
  123
  <ul>
    <li>abcd</li>
  </ul>
  <span>行内元素尽量只设置左右的内外边距</span>
</body>
```



![image-20240202195525713](http://images.newstar.net.cn/sally-imgsimage-20240202195525713.png)


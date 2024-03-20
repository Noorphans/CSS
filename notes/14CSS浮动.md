[toc]

# 

## 传统网页布局的三种方式

CSS 提供了**三种传统布局**方式(简单说,就是盒子如何进行排列顺序)：

1. 普通流（标准流）
2. 浮动
3. 定位

这三种布局方式都是用来摆放盒子的，盒子摆放到合适位置，布局自然就完成了。

> 注意：实际开发中，**一个页面基本都包含了这三种布局方式**（后面移动端学习新的布局方式） 。





## 标准流（普通流/文档流）

* **`所谓的标准流:  就是标签按照规定好默认方式排列`**

  1. 块级元素会独占一行，从上向下顺序排列。

     常用元素：div、hr、p、h1~h6、ul、ol、dl、form、table

  2. 行内元素会按照顺序，从左到右顺序排列，碰到父元素边缘则自动换行。

     常用元素：span、a、i、em 等 

* 以上都是标准流布局，我们前面学习的就是标准流，`标准流是最基本的布局方式`。





## 浮动float(重点)

### 为什么需要浮动？(重点)

* 提问：我们用标准流能很方便的实现如下效果吗？比较难
  1. 如何让多个块级盒子(div)水平排列成一行？

  * 转换为行内块元素可以实现一行显示，但是他们之间会有大的空白缝隙，很难控制，所以需要浮动float

  ```html
  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
     div {
        float: left;
        width: 150px;
        height: 200px;
        background-color: pink;
  
        /* 转为块级元素显示在一行 但盒子间有空隙 */
        /* display: inline-block; */
      }
    </style>
  </head>
  
  <body>
    <div>1</div>
    <div>2</div>
    <div>3</div>
  </body>
  ```

  

  ![image-20240228155306935](http://images.newstar.net.cn/sally-imgsimage-20240228155306935.png)

  

  

  2. 如何实现两个盒子的左右对齐？使用浮动

  ```html
  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
      .left,
      .right {
        float: left;
        width: 200px;
        height: 200px;
        background-color: pink;
      }
  
      .right {
        float: right;
      }
    </style>
  </head>
  
  <body>
    <div class="left">左青龙</div>
    <div class="right">右白虎</div>
  </body>
  ```



​         ![image-20240228155554146](http://images.newstar.net.cn/sally-imgsimage-20240228155554146.png)  







> **总结：**有很多的布局效果，标准流没有办法完成，此时就可以利用浮动完成布局。 因为浮动可以改变元素标签默认的排列方式.
>
> 1. 浮动最典型的应用：可以让多个块级元素一行内排列显示。
> 2. 网页布局第一准则：**`多个块级元素纵向排列找标准流，多个块级元素横向排列找浮动`**。







### 什么是浮动

* `float` 属性用于创建浮动框，将其移动到一边，直到左边缘或右边缘触及包含块或另一个浮动框的边缘。
  * (浮动是兄弟关系，只要加浮动就在一行显示)
  * 加浮动就移动到左边，右浮动就移动到右边
  * 若都是左浮动，就都移动到左边

* 语法：

```css
 选择器 { float: 属性值; }
```

![1571543209934](http://images.newstar.net.cn/sally-imgs1571543209934.png)





### 浮动特性（重难点）

加了浮动之后的元素,会具有很多特性,需要我们掌握的.

`1. 浮动元素会脱离标准流(脱标：浮动的盒子不再保留原先的位置)`

2. 浮动的元素会一行内显示并且元素顶部对齐
3. 浮动的元素会具有行内块元素的特性





### 浮动元素会脱离标准流(牢记重点)

* 设置了浮动（float）的元素最重要特性：

  1. 脱离标准普通流的控制（浮） 移动到指定位置（动）, （脱离标准流的控制俗称`脱标`）

     简单理解：浮即当我们给元素添加浮动后，它首先会脱离标准流的控制浮起来，并移动到所指定的位置，称为动。这是浮动的由来

     ![image-20240228175840428](http://images.newstar.net.cn/sally-imgsimage-20240228175840428.png) 

     

  2. (脱标)浮动的盒子`不再保留原先的位置`

     白话：飞到半空中的女孩和其他人不再是同一级别，女孩是浮动元素，剩下的人还是普通元素标准流。女孩飞走后 原来的位置会被其他元素认为不存在，不会保留她的位置，被标准流填补占据

     ![image-20240228180017426](http://images.newstar.net.cn/sally-imgsimage-20240228180017426.png) 

     \- 举例说明：

     ```html
     <head>
       <meta charset="UTF-8">
       <meta name="viewport" content="width=device-width, initial-scale=1.0">
       <title>浮动特性1</title>
       <style>
         /* 设置了浮动（float）的元素会：
         1. 脱离标准普通流的控制（浮）移动到指定位置（动）。
         2.浮动的盒子不在保留原先的位置 */
         .box1 {
           float: left;
           width: 200px;
           height: 200px;
           background-color: pink;
         }
     
         .box2 {
           width: 300px;
           height: 300px;
           background-color: rgb(0, 153, 255);
         }
       </style>
     </head>
     
     <body>
       <div class="box1">浮动的盒子</div>
       <div class="box2">标准流的盒子</div>
     </body>
     ```

     ![image-20240228180146734](http://images.newstar.net.cn/sally-imgsimage-20240228180146734.png) 





### 浮动的元素会一行内显示并且元素顶部对齐

如果多个盒子都设置了浮动，则他们会按照属性值 `一行内显示并顶端对齐排列`

![image-20240228175319108](http://images.newstar.net.cn/sally-imgsimage-20240228175319108.png)



\- 举例说明：

```html
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>浮动元素特性-浮动元素一行显示</title>
  <style>
    div {
      float: left;
      width: 200px;
      height: 200px;
      background-color: pink;
    }

    .two {
      background-color: purple;
      height: 249px;
    }

    .four {
      background-color: skyblue;
    }
  </style>
</head>

<body>
  <div>1</div>
  <div class="two">2</div>
  <div>3</div>
  <div class="four">4</div>
</body>
```



![image-20240228180407768](http://images.newstar.net.cn/sally-imgsimage-20240228180407768.png)

> **注意：** `浮动的元素是互相贴靠在一起的（不会有缝隙），如果父级宽度装不下这些浮动的盒子，多出的盒子会另起一行对齐。`





### 浮动的元素会具有行内块元素的特性

* 任何元素都可以浮动。不管原先是什么模式的元素，添加浮动后具有**`行内块元素`**相似特性。
* 也就是行内元素有了浮动,则不需要转换块级 或 行内块元素就可以直接给高度和宽度
  1. (**浮动元素的大小根据内容来决定**)如果块级盒子没有设置宽度，默认宽度和父级一样宽，但是添加浮动后，它的大小根据内容来决定
  2. **浮动的盒子中间是没有缝隙的**，是紧挨着一起的
  3. 行内元素同理



```html
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>浮动的元素具有行内块元素特点</title>
  <style>
    /* 任何元素都可以浮动。不管原先是什么模式的元素，添加浮动之后具有行内块元素相似的特性。 */
    span,
    div {
      float: left;
      width: 200px;
      height: 100px;
      background-color: pink;
    }

    /* 如果行内元素有了浮动,则不需要转换块级\行内块元素就可以直接给高度和宽度 */
    /* 块级盒子添加浮动后，盒子大小根据内容决定 */
    p {
      float: right;
      height: 200px;
      background-color: plum;
    }
  </style>
</head>

<body>
  <span>1</span>
  <span>2</span>

  <div>div</div>
  <p>ppppppp</p>
</body>
```



![image-20240229102023891](http://images.newstar.net.cn/sally-imgsimage-20240229102023891.png)







### 浮动元素经常和标准流父级搭配使用

> 为了约束浮动元素位置, 我们网页布局一般采取的策略是:
>
> 符合网页布局第一准侧:`先用标准流父元素排列上下位置, 之后内部子元素采取浮动排列左右位置.`
>
> 符合网页布局第二准侧：`先设置盒子的大小, 之后设置盒子的位置.`



![1571544991989](http://images.newstar.net.cn/sally-imgs1571544991989.png)

图解：先准备一个标准流的父盒子，独占一行放在页面中央，然后里面再放三个盒子加上浮动，显示在一行





\- 举例说明：

```html
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>浮动元素搭配标准流父盒子1</title>
  <style>
    .box {
      width: 900px;
      height: 260px;
      background-color: pink;
      margin: 0 auto;
    }

    .left {
      float: left;
      width: 300px;
      height: 260px;
      background-color: plum;
    }

    .right {
      float: left;
      /* 父级宽度装不下这些浮动的盒子，多出的盒子会另起一行对齐 */
      /* width: 770px; */
      width: 280px;
      height: 260px;
      background-color: skyblue;
    }

    .one {
      float: left;
      width: 300px;
      height: 260px;
      background-color: orange;
    }
  </style>
</head>

<body>
  <div class="box">
    <div class="left">浮动盒子1</div>
    <div class="right">浮动盒子2</div>
    <div class="one">浮动盒子3</div>
  </div>
</body>
```

![image-20240229110214020](http://images.newstar.net.cn/sally-imgsimage-20240229110214020.png)





### 浮动不会压住下面标准流盒子里的文字和图片

> **浮动产生最初的目的是做文字环绕效果**

1. 浮动不会压住下面标准流盒子里的文字

```css
<style>
    .box {
      float: left;
      width: 150px;
      height: 150px;
      background-color: plum;
    }
  </style>
</head>

<body>
  <div class="box"></div>
  <p>君不见黄河之水天上来</p>
</body>
```

![image-20240319172833135](http://images.newstar.net.cn/sally-imgsimage-20240319172833135.png) 

2. 浮动不会压住下面标准流盒子里的图片

```css
<style>
    .box {
      width: 200px;
      height: 200px;
      background-color: plum;
    }

    .sbox {
      width: 200px;
      height: 300px;
      background-color: skyblue;
    }
  </style>
</head>

<body>
  <div class="box"></div>
  <img src="../images/img.jpg" alt="">
</body>
```

![image-20240319172912001](http://images.newstar.net.cn/sally-imgsimage-20240319172912001.png) 
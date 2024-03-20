[toc]





## 绝对定位(absolute)-非常重要  

- **`绝对定位`**是元素在移动位置的时候，是相对于它`祖先元素`来说的（**拼爹型**）。

- 语法：

  ```css
   选择器 { 
   	position: absolute; 
   }
  ```

  > **绝对定位的特点：（务必记住）**
  >
  > 1. 若`无祖先元素`或者`祖先元素没有定位`，则以`浏览器为准`定位（Document 文档）。
  > 2. 也就是`父元素没有定位`，以`浏览器`为参照点移动。
  >
  > 3. 若父元素有定位（相对、绝对、固定定位），则以`最近一级有定位`的父元素为参考点移动位置。
  >
  > 4. **绝对定位`不再占有原先的位置`。（`完全脱标`——完全不占位置）**

  

### 没有祖先元素

若`无祖先元素`，则以`浏览器(Document文档-整个页面文档)为准`定位。

```css
<style>
    body {
      background-color: #999;
    }

    .son {
      position: absolute;
      /* 靠浏览器左上角 */
      top: 10px;
      left: 10px;

      /* 靠浏览器右上角 */
      /* top: 100px;
      right: 200px; */

      /* 浏览器左下角 */
      /* bottom: 0;
      left: 0; */
      width: 200px;
      height: 200px;
      background-color: pink;
    }
  </style>
</head>

<body>
  <div class="father">
    <div class="son"></div>
  </div>
```



![image-20240305190708974](http://images.newstar.net.cn/sally-imgsimage-20240305190708974.png)





### 有祖先元素，无定位

同样，以`浏览器为准`定位（Document 文档）

```css
  <style>
	/* 有父元素无定位 */
    .father {
      width: 500px;
      height: 500px;
      margin: 100px;
      background-color: skyblue;

    }

    .son1 {
      position: absolute;
      /* 靠浏览器左上角 */
      top: 40px;
      left: 200px;

      /* 靠浏览器右上角 */
      /* top: 100px;
      right: 200px; */

      /* 浏览器左下角 */
      /* bottom: 0;
      left: 0; */
      width: 200px;
      height: 200px;
      background-color: pink;
    }

	 /* 占据son1的位置 */
    .son2 {
      width: 200px;
      height: 200px;
      background-color: plum;
    }
  </style>
</head>

<body>
  <div class="father">
    <div class="son1">son1</div>
    <div class="son2">son2</div>
  </div>
</body>
```

![image-20240305165209233](http://images.newstar.net.cn/sally-imgsimage-20240305165209233.png)





### 祖先元素有定位

若祖先元素有定位（相对、绝对、固定定位），则以`最近一级有定位`的父元素为参考点移动位置。

```css
  <style>
    /* 以最近一级有定位的父元素为参考点 */
    .yeye {
      position: relative;
      width: 610px;
      height: 610px;
      padding: 50px;
      background-color: palegoldenrod;
    }


    .father {
      width: 600px;
      height: 600px;
      background-color: skyblue;
    }

    /* 父级有定位时不再以浏览器为准，而是在父盒子内部来回移动 */
    .son {
      position: absolute;
      left: 400px;
      bottom: 20px;
      width: 200px;
      height: 200px;
      background-color: pink;
    }
  </style>
</head>

<body>
  <div class="yeye">grandfather
    <div class="father">father
      <div class="son">son1</div>
    </div>
  </div>
</body>
```









### 脱离标准流 — 不占有原先的位置

```css
 <style>
    /* 以最近一级有定位的父元素为参考点 */
    .yeye {
      position: relative;
      width: 610px;
      height: 610px;
      padding: 50px;
      background-color: palegoldenrod;
    }


    .father {
      width: 600px;
      height: 600px;
      background-color: skyblue;
    }

    /* 父级有定位时不再以浏览器为准，而是在父盒子内部来回移动 */
    .son1 {
      position: absolute;
      left: 400px;
      bottom: 20px;
      width: 200px;
      height: 200px;
      background-color: pink;
    }

    .son2 {
      width: 200px;
      height: 200px;
      background-color: plum;
    }

    .son3 {
      width: 200px;
      height: 200px;
      background-color: aqua;
    }
  </style>
</head>

<body>
  <div class="yeye">grandfather
    <div class="father">father
      <div class="son1">son1</div>
      <div class="son2">son2</div>
      <div class="son3">son3</div>
    </div>
  </div>
</body>
```



![image-20240305193707104](http://images.newstar.net.cn/sally-imgsimage-20240305193707104.png)





## 绝对定位和相对定位的使用场景

因为`绝对定位`的盒子是`拼爹`的，所以要和`父级搭配`一起`使用`。

> **定位口诀**: **`子绝父相`** —— `子`级使用`绝`对定位，`父`级使用`相`对定位







### 子绝父相的由来

  1. 子级绝对定位，不会占有位置，可以放到父盒子里面的任何一个地方，不会影响其他的兄弟盒子。

  2. 父盒子需要加定位限制子盒子在父盒子内显示。

  3. 所以`相对定位`经常用来`作为绝对定位的父级`。


> 总结： 
>
> 1. `父级需要占有位置`，所以用`相对定位`。子盒子`不需要占有位置`，任意摆放，所以用`绝对定位`
> 2. 如父元素不需要占有位置，`子绝父绝，子相父绝`也会遇到(但很少用到)。







### 为什么说相对定位给绝对定位当爹的呢？

1. 子级绝对定位，不会占有位置，可放到父盒子里任何一个地方，不会影响其他的兄弟盒子。
2. 父盒子需要加定位限制子盒子在父盒子内显示
3. **父盒子布局时，需要占有位置，因此父亲只能是相对定位**
4. 这就是子绝父相的由来，所以`相对定位经常用来作为绝对定位的父级`。





### 为什么在布局时，使用子绝父相呢？

>`因为父级需要占有位置，因此是相对定位， 子盒子不需要占有位置，则是绝对定位`



* 观察下图，思考一下在布局时，**左右两个方向的箭头图片**以及**父级盒子**的定位方式。

 ![image-20240305211748105](http://images.newstar.net.cn/sally-imgsimage-20240305211748105.png)



**分析：**

1. 只有左右箭头 添加浮动可以。

   * 但如果图片是先插入的，再给两盒子加浮动，那么它们就在图片下面显示，因为`浮动只会影响它后面的盒子,不会影响前面的盒子`.总是靠近前面盒子的下边缘显示

   * 如果左右箭头和小圆点 都加上浮动，就会在一行显示，所以浮动很难布局这个效果

     

2. 所以**方向箭头和小圆点**叠加在其他图片上方，`子级`使用`绝对定位`，因为绝对定位`完全脱标`，完全不占位置.

   * 但是**父盒子没有定位**，这三个盒子**就会超出**父盒子范围移动到其他位置显示

     

3. `父级`盒子应该使用`相对定位`，因为相对定位`不脱标`，**占据位置**，按标准流方式显示，不影响后面盒子的正常显示。

   * 我们想要的是三个盒子必须在父盒子内，所以`父`盒子要加`相对定位`**限制**三个**子盒子**在父盒子内显示
   * 如果父元素大盒子子也使用**绝对定位**，会完全脱标，父元素后面又还有其他的兄弟盒子，那么就会顶替父元素的位置，后面盒子上移跑到父元素的底下去，被父元素覆盖，这显然不是我们想要的。









## 绝对定位的盒子居中

加了绝对定位的盒子不能通过 margin:0 auto 水平居中，但是可以通过以下计算方法实现水平和垂直居中。

1. left: 50%;：让盒子的左侧移动到父级元素的水平中心位置。

2. margin-left: -100px;：让盒子向左移动自身宽度的一半

```css
  <style>
    .box {
      position: relative;
      width: 800px;
      height: 400px;
      background-color: palegoldenrod;
    }

    .sbox {
      width: 200px;
      height: 100px;
      background-color: pink;
    }

    /* 1号水平居中靠上对齐 */
    .son1 {
      position: absolute;
      left: 50%;
      margin-left: -100px;

    }

    /* 2号水平居中靠下对齐 */
    .son2 {
      position: absolute;
      left: 50%;
      margin-left: -100px;
      /* 靠下对齐 再加上两个子盒占位宽度200 */
      margin-top: 300px;
      /* 简写 */
      /* margin: 300px -100px; */

    }

    /* 3号垂直居中靠左对齐*/
    .son3 {
      position: absolute;
      top: 50%;
      margin-top: -50px;
    }

    /* 4号垂直居中靠右对齐 */
    .son4 {
      position: absolute;
      top: 50%;
      margin-top: -50px;
      /* 靠右对齐 再加上两个子盒占位宽度400 */
      margin-left: 600px;
      /* margin: -50px 600px; */
    }

    /* 5号水平垂直居中对齐 */
    .son5 {
      position: absolute;
      left: 50%;
      top: 50%;
      margin-left: -100px;
      margin-top: -50px;
    }
  </style>
</head>

<body>
  <div class="box">
    <div class="sbox son1">1号水平居中靠上对齐</div>
    <div class="sbox son2">2号水平居中靠下对齐</div>
    <div class="sbox son3">3号垂直居中靠左对齐</div>
    <div class="sbox son4">4号垂直居中靠右对齐</div>
    <div class="sbox son5">5号水平垂直居中对齐</div>
  </div>
</body>
```

![image-20240319174656686](http://images.newstar.net.cn/sally-imgsimage-20240319174656686.png)





## 绝对定位会压住下面标准流所有的内容

* 固定定位同理

```css
<style>
    .box {
      /* 2. 绝对定位（固定定位） 会压住下面标准流所有的内容。 */
      /* position: fixed; */
      position: absolute;
      width: 200px;
      height: 200px;
      background-color: aqua;
    }
  </style>
</head>

<body>
  <div class="box"></div>
  <p>阁下何不同风起，扶摇直上九万里</p>
</body>
```

![image-20240319175339238](http://images.newstar.net.cn/sally-imgsimage-20240319175339238.png)
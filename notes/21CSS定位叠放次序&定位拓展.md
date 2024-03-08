[toc]



## 定位叠放顺序（z-index）

- 在使用**定位**布局时，可能会**出现盒子重叠的情况**。
- 此时，可以使用 `z-index` 来**控制盒子的前后次序** (z轴)

![image-20240306213221133](http://images.newstar.net.cn/sally-imgsimage-20240306213221133.png) 

- 语法：

  ```css
  选择器 { 
  	z-index: 1; 
  }
  ```

  

- `z-index` 的特性如下：

  1. 属性值：正整数**、**负整数 或0，默认值是 0，`数值越大，盒子越靠上`；	
  2. 如果`属性值相同`，则按照书写顺序，`后来者居上`；
  3. **数字**后面`不能加单位`。
  4. 只有定位的盒子才有 z-index 属性

  

  > **注意**：`z-index` 只能应用于**`相对定位、绝对定位和固定定位`**的元素，其他**标准流**、**浮动**和**静态定位**无效。



- 应用 `z-index` 层叠等级属性可以**调整盒子的堆叠顺序**。如下图所示：

![12_zindex示意图](http://images.newstar.net.cn/sally-imgs12_zindex%E7%A4%BA%E6%84%8F%E5%9B%BE.png)



\- 举例说明：

```css
<style>
    /* 三个盒子都加了绝对定位 会出现堆叠情况*/
    .box {
      position: absolute;
      top: 0;
      left: 0;
      width: 200px;
      height: 200px;
    }

    .xiongda {
      background-color: red;
      z-index: 1;
    }

    .xionger {
      left: 50px;
      top: 50px;
      background-color: green;
      z-index: 2;
    }

    .qiangge {
      left: 100px;
      top: 100px;
      background-color: blue;
    }
  </style>
</head>

<body>
  <div class="box xiongda">熊大</div>
  <div class="box xionger">熊二</div>
  <div class="box qiangge">光头强</div>
</body>
```

**分析：**

1. box加绝对定位，相当于三个盒子都绝对定位
2. top：0， left：0 ，第一个盒子先跑到这个位置，后面的跟着跑过来，就会出现堆叠在一起的情况
3. 因为属性都一样，所以后来者居上，1号盒子设置z-index: 1;就会显示在最上面
4. 当2号盒子设置 z-index: 2;那么2号盒子就会在最上面，`数值越大，盒子越靠上`



![image-20240306215226440](http://images.newstar.net.cn/sally-imgsimage-20240306215226440.png)



## 定位拓展

### 绝对/固定定位的盒子居中

> **注意**：加了**绝对定位/固定定位的盒子**不能通过设置 `margin: auto` 设置**水平居中**。
>
> 但是可以通过以下计算方法实现水平和垂直居中，可以按照下图的方法：



![](http://images.newstar.net.cn/sally-imgsimage-20240307105502516.png)

**分析：**

1. `left: 50%;`：让**盒子的左侧**移动到**父级元素的水平中心位置**；
2. `margin-left: -100px;`：让盒子**向左**移动**自身宽度的一半**。



\- 举例说明：

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



* **分析：**
  1. 1号子盒水平居中靠上：先左移动父盒宽度的一半50% 即w400px，左外边距再移动自身宽度的一半 -100px
  2. 2号子盒水平居中靠下：先同步1号子盒操作 到1号子盒的位置，再上外边距移动300px到父盒底部，300px也就是加上1号子盒和5号子盒的占位高度100+100+100
  3. 3号子盒垂直居中靠左：先上移动父盒高度的一半50% 即200px，上外边距再移动自身高度一半-50px
  4. 4号子盒垂直居中靠右：先同步3号子盒操作 到3号子盒的位置，再左外边距移动600px到父盒右边，600px也就是加上3号子盒和5号子盒的占位宽度200+200+200
  5. 5号子盒水平垂直居中：先同步1号子盒操作，再同步2号子盒操作



* 示意图：

![image-20240307120012792](http://images.newstar.net.cn/sally-imgsimage-20240307120012792.png)



![image-20240307120034771](http://images.newstar.net.cn/sally-imgsimage-20240307120034771.png)





### 定位特殊性

> 绝对定位和固定定位 也和浮动类似。
>
> 1. `行内元素`添加`绝对或者固定定位`，可以`直接设置高度和宽度`。
>
> 2. `块级元素`添加`绝对或者固定定位`，如果`不给宽度或者高度，默认大小是内容的大小`。



* 前面知识点， display 是 显示模式， 可以改变显示模式有以下方式:
  1. 可以用inline-block  转换为行内块
  2. 可以用浮动 float 默认转换为行内块（类似，并不完全一样，因为浮动是脱标的）
  3. 绝对定位和固定定位也和浮动类似， 默认转换的特性 转换为行内块。

> **注意：** 一个`行内的盒子`，如果加了**`浮动`**、**`固定定位`**和**`绝对定位`**，**不用转换**，就可以给这个盒子**直接设置宽度和高度**等。

```css
<style>
    span {
      position: absolute;
      top: 300px;
      width: 200px;
      height: 150px;
      background-color: pink;
    }

    div {
      position: absolute;
      background-color: skyblue;
    }
  </style>
</head>

<body>
  <!-- 行内元素添加绝对定位，不用转换直接设置宽高-->
  <span>123</span>

  <!-- 块级元素添加绝对定位，不给宽高，默认大小是内容的大小-->
  <div>abcddsgfsgd</div>
</body>
```





### 脱标的盒子不会触发外边距塌陷

* `浮动元素、绝对定位/固定定位元素`的都`不会触发外边距合并`的问题。 
* 以前是用padding border overflow解决的,**现在**盒子`改为`了`浮动或者定位`，就`不会有垂直外边距合并`的问题了。





### 浮动只会压住盒子，不会压住下面的文字图片

> * 浮动元素不同的是，`只会压住它下面标准流的盒子`，但是`不会压住`下面标准流盒子`里面的文字或图片`
> * 浮动之所以不会压住文字，因为`浮动产生的目的`最初是为了`做文字环绕效果的`。**文字会围绕浮动元素**

1. 不会压住下面标准流盒子里的文字-`浮动产生最初的目的是做文字环绕效果`

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



![image-20240307141612704](http://images.newstar.net.cn/sally-imgsimage-20240307141612704.png)

2. 不会压住下面标准流盒子里的图片

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



![image-20240307143914139](http://images.newstar.net.cn/sally-imgsimage-20240307143914139.png)





   

   

### 绝对定位&固定定位会压住下面标准流所有的内容

> 绝对定位（固定定位）会完全压住标准流盒子内容

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



![image-20240307144857500](http://images.newstar.net.cn/sally-imgsimage-20240307144857500.png)
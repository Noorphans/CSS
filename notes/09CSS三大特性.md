# CSS 的三大特性

[toc]





CSS 有三个**非常重要**的三个特性：**层叠性、继承性、优先级**



## 层叠性

* **相同选择器**给设置**相同样式**，此时一个样式就**会覆盖**（**层叠**）另一个**冲突**的样式。`层叠性主要解决样式冲突的问题`

* CSS 层叠性口诀：**`长江后浪推前浪，前浪死在沙滩上`**。

* 层叠性原则：

  1. 样式冲突，遵循的原则是`就近原则`，哪个样式离结构近，就执行哪个样式
  2. 样式不冲突，不会层叠

  ![1571490015544](http://images.newstar.net.cn/sally-imgs1571490015544.png)

   ![image-20240126184438829](http://images.newstar.net.cn/sally-imgsimage-20240126184438829.png)







## 继承性

现实中的继承: 我们继承了父亲的姓

CSS中的继承: **子标签**会**继承父标签**的`某些样式`，如文本颜色和字号。简单的理解就是：**子承父业**

![1571490049279](http://images.newstar.net.cn/sally-imgs1571490049279.png)

>* 恰当地使用继承可以简化代码，降低 CSS 样式的复杂性
>* **子元素可以继承父元素的样式**（`text-，font-，line-这些元素开头的可以继承，以及color属性`、visibility可见性属性、border-collapse表格布局属性）





### 行高的继承性

> 行高会继承

1. 若想把两个并集标签 都改为相同样式怎么做？

  * 直接给他们的父元素设置样式，让两个子元素继承父元素

  ```html
   <style>
      body {
        color: pink;
  
        /* 行高跟单位继承 */
        /* font: 12px/24px 'Microsoft YaHei'; */
  
        /* 行高不带单位继承 */
        font: 12px/1.5 'Microsoft YaHei';
      }
    </style>
  </head>
  
  <body>
    <!-- 继承body的样式 -->
    <div>青少年</div>
    <p>青少年</p>
  </body>
  ```



2. **`行高可以跟单位也可以不跟单位`**

![image-20240127184645973](http://images.newstar.net.cn/sally-imgsimage-20240127184645973.png) 

  >   * 如果`子元素没有设置行高`，则会`继承父元素的行高1.5`(此时子元素的行高是：**当前子元素**的`文字大小 * 1.5` )
  >   * **`body 行高 1.5 `这样写法最大的优势就是`里面子元素可以根据自己 文字大小 自动调整行高`**(文字大则行高自动变大)



\- 举例说明：

```html
 <style>
    body {
      color: pink;

      /* 行高跟单位继承 */
      /* font: 12px/24px 'Microsoft YaHei'; */

      /* 行高不带单位继承 */
      font: 12px/1.5 'Microsoft YaHei';
    }

    div {
      /* 子元素继承了父元素body 的行高1.5 */
      /* 也就是当前子元素的文字大小font-size 的1.5倍，21像素  */
      font-size: 14px;
    }

    p {
      /* 1.5*16 =24*/
      font-size: 16px;
    }

    /* 没有手动指定文字大小 继承父元素body的12px，行高也继承body的1.5 */
    /* 所以当前li的行高就是 1.5*12  */
    li {}
  </style>
</head>

<body>
  <!-- 继承body的样式 -->
  <div>青少年</div>
  <p>青少年</p>
  <ul>
    <li>没有指定文字大小</li>
  </ul>
</body>
```

**解析：**

1. div子元素 继承父元素body的行高1.5，*1.5就是**当前子元素**的文字大小font-size 的1.5倍*，所以当前div行高就是21像素
2. p子元素继承父元素行高1.5倍，为24px
3. li子元素*没有手动指定文字大小 继承父元素body的12px，行高也继承body的1.5*，*所以当前li的行高就是 1.5\*12=18px*

​      





## 优先级

目标：能够计算CSS的权重

当同一个元素指定多个选择器，就会有优先级的产生。

* 选择器相同，则执行层叠性
* 选择器不同，则根据`选择器权重`执行

![1571490129794](http://images.newstar.net.cn/sally-imgs1571490129794.png)

> 属性选择器 同 类选择器、伪类选择器权重一样，也是0010



\- 举例说明：

```html
<style>
    /* !important权重比最大 */
    div {
      color: red;
    }

    .test {
      color: aqua !important;
    }

    #demo {
      color: pink;
    }
  </style>
</head>

<body>
  <div class="test" id="demo" style="color: plum;">你笑起来真好看</div>
</body>
```







### 优先级注意点(重点)

* 权重是有**4组数字**组成,但是**不会有进位**

  1. 可以理解为类选择器永远大于元素选择器, id选择器永远大于类选择器,后面的永远大于前面的，以此类推.
  2. 等级判断从左向右，如果某一位数值相同，则判断下一位数值。

  > **简单记忆法:** 通配符和继承权重为0, 标签选择器为1,类和伪类选择器为 10, id选择器 100, 行内样式表为
  >
  > 1000, !important 无穷大

  

*  **`继承的权重是0`**， 如果该元素没有直接选中，**不管父元素权重多高，子元素得到的权重都是 0**。



\- 举例说明: 

* ID选择器权重为0100 大于标签选择器权重为0001，为什么还是执行标签选择器？

  因为 父元素权重是100，但p继承的权重为0，重新给p单独设置个样式即标签选择器，也就是本身权重1比0大，所以执行p

```html
<style>
    /* 父元素权重是100 */
    #father {
      color: pink;
    }

    /* 继承权重是0 */
    /* 单独设置样式为标签选择器，权重为1 ，所以是红色 */
    p {
      color: red;
    }
    
    /* a链接浏览器默认制定了一个样式 蓝色的 有下划线  a {color: blue;}*/
    a {
      color: green;
    } 
  </style>
</head>

<body>
  <div id="father">
    <p>你还是那么好看</p>
  </div>
  <a href="#">a链接 我是单独的样式</a>  
</body>
```

> **注：** 
>
> * `标签(元素)选择器`到底`执行`哪个样式，就先看这个样式`是否直接`被选出来`单独设置样式`(**优先执行被选出来的样式**)
> * `a链接`浏览器`默认`制定了一个样式 `蓝色的 有下划线`  a {color: blue;}，**`需要重新设置样式`**





### 权重叠加(重点)

权重叠加：如果是`复合选择器`，则会`有权重叠加`，需`要计算权重`。

```html
 <style>
    /* 复合选择器 权重叠加， 权重虽会叠加,但是永远不会有进位  */
    /* ul li 权重  0,0,0,1 + 0,0,0,1  =  0,0,0,2     2 */
    ul li {
      color: skyblue;
    }

    /* li 的权重是 0,0,0,1    1 */
    li {
      color: red;
    }

    /* .nav li  权重    0,0,1,0  +  0,0,0,1  =  0,0,1,1    11 */
    .nav li {
      color: pink;
    }
  </style>

</head>

<body>
  <ul class="nav">
    <li>大猪蹄子</li>
    <li>大肘子</li>
    <li>猪尾巴</li>
  </ul>
</body>
```

> **注：**
>
> * `复合选择`会`有权重叠加`的问题,但`永远不会有进位`(4组数为单位)
>   * 比如，有10个标签选择器累加就是00010，最后两位是10，永远比不过类选择器0010



\- 举例说明： 

* div ul li  ----->  0001+0001+0001= 0,0,0,3
* .nav ul li ----->  0010+0001+0001= 0,0,1,2
* a:hover    ----—>  0001+0010= 0,0,1,1
* .nav a     ----->  0010+0001= 0,0,1,1



> 当**样式冲突**的时候，选择器的**权重大**则该选择器下面的样式**起作用**,**权重越高，优先执行**





> 比较思路：
>
> 1. 先判定是否是直接选择到目标标签(直接选中也就是直接为目标标签设置样式，不是继承)
> 2. 如果不是继承，再计算选择器的权重大小
> 3. 当两个选择器权重相同的时候，离标签最近的起作用


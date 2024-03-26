[toc]





## rem基础

* **思考：** 选哪种方案 ？
  1. 页面布局文字能否随着屏幕大小变化而变化？
     * 文字不变
  2. 流式布局和flex布局主要针对于宽度布局，那高度如何设置？
     * 高度定死，写死
  3. 怎么样让屏幕发生变化的时候元素高度和宽度等比例缩放？
     * 使用rem+媒体查询





### rem 单位

* rem (root em)是一个相对单位，类似于em，`em`是`父元素`**字体大小**。

```css
<style>
        div {
            font-size: 12px;
        }

        p {
            /* 1. em相对于父元素的 字体大小来说的 ,
            em是12像素，10em是10*12等于120em*/
            width: 10em;
            height: 10em;
            background-color: pink;
        }
    </style>
</head>

<body>
    <div>
        <p></p>
    </div>
</body>
```



* 不同的是`rem`的基准`是`相对于**`html元素`**的`字体大小`。

* root是根的意思，而我们整个页面有一个根元素就是html元素，所以是相对于html元素的

  * 比如，根元素（html）设置font-size=12px; 非根元素设置width:2rem; 则换成2rem就是24像素。
  * 比如，页面中每个盒子大小都不一样，把盒子中的单位都改为rem，在不同的屏幕宽度下，只需要更改html的文字大小，每个盒子就会跟着一起变。
  * 当你屏幕变大，html里的文字就变大一些，那里面的子盒子宽高就变得大一些。
  * 当你屏幕变小，html里的文字就变小一些，那里面的盒子都会一起变小

  ```css
   html {
        font-size: 10px;
      }
  
      div {
        font-size: 12px;
        width: 15rem;
        height: 15rem;
        background-color: plum;
      }
  
      p {
        /*  1.rem 相对于 html元素 字体大小来说的 */
        width: 10rem;
        height: 10rem;
        background-color: pink;
      }
    </style>
  </head>
  
  <body>
    <div>
      <p></p>
    </div>
  </body>
  ```

  ![image-20240324131704064](http://images.newstar.net.cn/sally-imgsimage-20240324131704064.png) 

  



> **rem的优势：** 父元素文字大小可能不一致，整个页面只有一个html元素，通过**修改html元素里的文字大小来控制整个页面的元素大小**









## 媒体查询

### 什么是媒体查询

媒体查询（**`Media Query`**）是CSS3新语法。

* 使用 @media 查询，可以针对不同的媒体类型定义不同的样式
* `@media 可以针对不同的屏幕尺寸设置不同的样式`
* 当你重置浏览器大小的过程中，页面也会根据浏览器的宽度和高度重新渲染页面
* 目前针对很多苹果手机、Android手机，平板等设备都用得到多媒体查询





### 语法规范

```css
@media mediatype and|not|only (media feature) {
 CSS-Code;
}
```

* 用 @media 开头 注意@符号
* mediatype 媒体类型
* 关键字 and not only
* media feature 媒体特性 必须有小括号包含





#### mediatype 媒体查询

将不同的终端设备划分成不同的类型，称为**媒体类型**

![image-20240324153639176](http://images.newstar.net.cn/sally-imgsimage-20240324153639176.png) 



#### 关键字

关键字将媒体类型或多个媒体特性连接到一起做为媒体查询的条件

* and：可以将多个媒体特性连接到一起，相当于“且”的意思。
* not：排除某个媒体类型，相当于“非”的意思，可以省略。
* only：指定某个特定的媒体类型，可以省略。 





#### 媒体特性

每种媒体类型都具体各自不同的特性，根据不同媒体类型的媒体特性设置不同的展示风格。我们暂且了解三个。

> **注意**：他们要加**小括号**包含

![image-20240324154323090](http://images.newstar.net.cn/sally-imgsimage-20240324154323090.png) 



\- 举例说明：

```css
<style>
        /* 这句话的意思就是： 在我们屏幕上 并且 最大的宽度是 800像素 设置我们想要的样式 */
        /* 也就是小于等于800 */
        /* 媒体查询可以根据不同的屏幕尺寸在改变不同的样式 */

        @media screen and (max-width:800px) {
            body {
                background-color: plum;
            }
        }


        @media screen and (max-width:500px) {
            body {
                background-color: pink;
            }
        }
    </style>
</head>
```

![image-20240324155716043](http://images.newstar.net.cn/sally-imgsimage-20240324155716043.png) 



> **注：** 
>
> 1. **`screen`** 还有 **`and`** 必须带上`不能省略`，**数字**后面必须**带单位**
> 2. 为了防止混乱，媒体查询我们要按照**从小到大或者从大到小的顺序来写**,但是我们最喜欢的**顺序**还是`从小到大`来写，这样代码更简洁



![image-20240324162415680](http://images.newstar.net.cn/sally-imgsimage-20240324162415680.png)







### 媒体查询+rem实现元素动态大小变化

* rem单位是跟着html来走的，有了rem页面元素可以设置不同大小尺寸
* 媒体查询可以根据不同设备宽度来修改样式
* 媒体查询+rem 就可以实现不同设备宽度，实现页面元素大小的动态变化



\- 举例说明：

```css
<style>
        * {
            margin: 0;
            padding: 0;
        }

        /* 这样把大小定死，我们要的是不同屏幕不同大小 */
        /* html {
            font-size: 100px;
        } */

        /* 从小到大的顺序 */
        @media screen and (min-width: 320px) {
            html {
                font-size: 50px;
            }
        }

        @media screen and (min-width: 640px) {
            html {
                font-size: 100px;
            }
        }

        .top {
            height: 1rem;
            background-color: green;
            /* html文字大小的一半 */
            font-size: .5rem;
            line-height: 1rem;
            color: #fff;
            text-align: center;
        }
    </style>
</head>

<body>
    <div class="top">购物车</div>
</body>
```









###  引入资源（理解）

当样式比较繁多的时候，我们可以针对不同的媒体使用不同 stylesheets（样式表）。

原理，就是直接在link中判断设备的尺寸，然后引用不同的css文件



#### 语法规范

```css
<link rel="stylesheet" media="mediatype and|not|only (media feature)" href="mystylesheet.css">
```





#### 示例

* 针对不同屏幕调用不同尺寸样式
* 当我们屏幕大于等于 640px以上的，我们让div 一行显示2个
* 当我们屏幕小于640， 我们让div一行显示一个





1. CSS外部样式 大于等于640的， div一行显示一个

```css
div {
    width: 100%;
    height: 100px;
}

div:nth-child(1) {
    background-color: pink;
}

div:nth-child(2) {
    background-color: plum;
}
```

2. CSS外部样式 小于640px的

```css
div {
    float: left;
    width: 50%;
    height: 100px;
}

div:nth-child(1) {
    background-color: pink;
}

div:nth-child(2) {
    background-color: plum;
}
```

3. HTML结构：

```html
<body>
    <div>1</div>
    <div>2</div>
</body>
```

4. 引入资源：

```css
<link rel="stylesheet" href="../CSS/style320.css" media="screen and (min-width: 320px)">
<link rel="stylesheet" href="../css/style640.css" media="screen and (min-width: 640px)">
```


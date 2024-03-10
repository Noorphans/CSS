[toc]





# CSS高级技巧

## 常见布局技巧

**巧妙利用一个技术更快更好的布局：**

1. margin负值的运用
2. 文字围绕浮动元素
3. 行内块的巧妙运用
4. CSS三角强化



###  margin负值运用

1. 问题：下面每个盒子都有细线边框，是给每个盒子加边框吗或去掉右边框吗？

   * 每个盒子都加边框的话，相邻边框加一起变成2px

   * 如果添加浮动，相邻边框就会重叠变为2px
   * 去掉边框也不行，最后一个是完整的4边框



![image-20240310172829804](http://images.newstar.net.cn/sally-imgsimage-20240310172829804.png) 



2. **解决方案：每个盒子加上左浮动，margin-left为-1px**

```css
 <style>
        ul li {
            /* 鼠标经过的颜色边框显示在上面 */
            position: relative;
            float: left;
            list-style: none;
            width: 150px;
            height: 200px;
            border: 1px solid red;
            margin-left: -1px;
        }

        /* ul li:hover {
           1. 如果盒子没有定位，则鼠标经过添加相对定位即可
        position: relative;
        border: 1px solid blue;

       } */
        ul li:hover {
            /* 2.如果li都有定位，则利用 z-index提高层级 */
            z-index: 1;
            border: 1px solid blue;
        }
    </style>
</head>

<body>
    <ul>
        <li>1</li>
        <li>2</li>
        <li>3</li>
        <li>4</li>
        <li>5</li>
    </ul>
</body>
```

> **鼠标经过某个盒子的时候，提高当前盒子的层级即可**
>
> 1. 如果没有有定位，则加相对定位（保留位置）
> 2. 如果有定位，则加z-index 

![image-20240310194258344](http://images.newstar.net.cn/sally-imgsimage-20240310194258344.png) 



### 文字围绕浮动元素

* 以前我们会给两个盒子一个左浮动 一个右浮动，现在**可以巧妙运用浮动元素不会压住文字的特性**
  1. 准备一个大盒子，文字就以标准流放进大盒子里
  2. 在准备一个盒子放照片，添加一个左浮动，文字自然围绕图片在右侧显示

* **效果图：**

![image-20240310194433941](http://images.newstar.net.cn/sally-imgsimage-20240310194433941.png) 

* **布局示意图**：

![image-20240310194641669](http://images.newstar.net.cn/sally-imgsimage-20240310194641669.png) 

* 代码参考：

```css
<style>
        * {
            margin: 0;
            padding: 0;
        }

        .box {
            width: 300px;
            height: 70px;
            margin: 0 auto;
            padding: 5px;
            background-color: pink;
        }

        .pic {
            float: left;
            width: 120px;
            height: 60px;
            margin-right: 5px;
        }

        .pic img {
            width: 100%;
        }
    </style>
</head>

<body>
    <div class="box">
        <div class="pic">
            <img src="../images/img.png" alt="">
        </div>
        <p>【集锦】热身赛-巴西0-1秘鲁 内马尔替补两人血染赛场</p>
    </div>
</body>
```

![image-20240310195905697](http://images.newstar.net.cn/sally-imgsimage-20240310195905697.png) 





### 行内块巧妙运用

![1571522898744](http://images.newstar.net.cn/sally-imgs1571522898744.png)



#### 页码在页面中间显示

> 1. 把这些`链接盒子转换为行内块`，`之后给父级指定 text-align:center;`
> 2. 利用行内块元素中间有缝隙，并且给父级添加text-align:center; 行内块元素会水平会居中



![1571522910580](http://images.newstar.net.cn/sally-imgs1571522910580.png)



\- 举例说明：

```css
<style>
        * {
            margin: 0;
            padding: 0;
        }

        .box {
            margin: 50px auto;
            text-align: center;
        }

        .box a {
            display: inline-block;
            width: 36px;
            height: 36px;
            border: 1px solid #ccc;
            background-color: #f7f7f7;
            font-size: 14px;
            color: #333;
            line-height: 36px;
            text-decoration: none;
            text-align: center;
        }

        .box .prev,
        .box .next {
            width: 85px;
        }

        .box .current,
        .box .elp {
            border: 0;
            background-color: #fff;
        }

        .box input {
            width: 45px;
            height: 36px;
            border: 1px solid #ccc;
            outline: none;
        }

        .box button {
            width: 60px;
            height: 36px;
            border: 1px solid #ccc;
            background-color: #f7f7f7;
        }
    </style>
</head>

<body>
    <div class="box">
        <a href="#" class="prev">&lt;&lt;上一页</a>
        <a href="#" class="current">2</a>
        <a href="#">3</a>
        <a href="#">4</a>
        <a href="#">5</a>
        <a href="#">6</a>
        <a href="#" class="elp">...</a>
        <a href="#" class="next">&gt;&gt;下一页</a>
        到第
        <input type="text">
        页
        <button>确定</button>
    </div>
</body>
```

![image-20240310202126637](http://images.newstar.net.cn/sally-imgsimage-20240310202126637.png) 





### CSS 三角强化

* 示例图：

![image-20240310202722277](C:\Users\Sally\AppData\Roaming\Typora\typora-user-images\image-20240310202722277.png) 

* 直角三角形原理：

![image-20240310202840267](http://images.newstar.net.cn/sally-imgsimage-20240310202840267.png) 

* 代码：

![image-20240310204918334](http://images.newstar.net.cn/sally-imgsimage-20240310204918334.png) 

> 1. 只保留右边的边框有颜色
>
> 2. 样式都是solid
>
> 3. 上边框宽度要大， 右边框 宽度稍小， 其余的边框该为 0

 

\- 举例说明：

* CSS样式：

```css
/* 案例秒杀模块 */
.price {
    width: 160px;
    height: 24px;
    margin: 0 auto;
    border: 1px solid red;
    line-height: 24px;
}

.miaosha {
    position: relative;
    /* span是行内元素，设置大小就要模式转换，
    但这两个刚好在一行上，直接利用浮动文字环绕特性*/
    float: left;
    width: 90px;
    height: 100%;
    margin-right: 8px;
    background-color: red;
    font-weight: 700;
    color: #fff;
    text-align: center;
}

/* i制作三角 */
.miaosha i {
    position: absolute;
    right: 0;
    top: 0;
    width: 0;
    height: 0;
    border-color: transparent white transparent transparent;
    border-style: solid;
    border-width: 24px 10px 0 0;
}

.origin {
    font-size: 12px;
    color: gray;
    text-decoration: line-through;
}
```

* HTMl结构

```html
<body>
    <div class="box1"></div>
    <!-- 案例 -->
    <div class="price">
        <span class="miaosha">
            ¥1650
            <i></i>
        </span>
        <span class="origin">¥5650</span>
    </div>
</body>
```







## CSS初始化

* 用于`消除不同浏览器之间的默认样式差异`，并`为网页提供一个统一的基础样式`。

* 不同浏览器对有些标签的默认值是不同的，为了消除不同浏览器对HTML文本呈现的差异，照顾浏览器的兼容，我们需要对CSS 初始化

* 简单理解：CSS初始化是指重设浏览器的样式。 (也称为CSS reset）

  1. 每个网页都必须首先进行 CSS初始化。
  2. 这里我们以 京东CSS初始化代码为例。

  ```css
  /* 把我们所有标签的内外边距清零 */
  * {
      margin: 0;
      padding: 0
  }
  
  /* em 和 i 斜体的文字不倾斜 */
  em,
  i {
      font-style: normal
  }
  
  /* 去掉li 的小圆点 */
  li {
      list-style: none
  }
  
  img {
      /* border 0 照顾低版本浏览器 如果 图片外面包含了链接会有边框的问题 */
      border: 0;
      /* 取消图片底侧有空白缝隙的问题 */
      vertical-align: middle
  }
  
  button {
      /* 当我们鼠标经过button 按钮的时候，鼠标变成小手 */
      cursor: pointer
  }
  
  a {
      color: #666;
      text-decoration: none
  }
  
  a:hover {
      color: #c81623
  }
  
  button,
  input {
      /* "\5B8B\4F53" 就是宋体的意思 这样浏览器兼容性比较好 */
      font-family: Microsoft YaHei, Heiti SC, tahoma, arial, Hiragino Sans GB, "\5B8B\4F53", sans-serif
  }
  
  body {
      /* CSS3 抗锯齿形 让文字显示的更加清晰 -了解*/
      -webkit-font-smoothing: antialiased;
      background-color: #fff;
      font: 12px/1.5 Microsoft YaHei, Heiti SC, tahoma, arial, Hiragino Sans GB, "\5B8B\4F53", sans-serif;
      color: #666
  }
  
  /* 京东自己定义的样式，隐藏元素 */
  .hide,
  .none {
      display: none
  }
  
  /* 清除浮动 伪元素*/
  .clearfix:after {
      visibility: hidden;
      clear: both;
      display: block;
      content: ".";
      height: 0
  }
  
  .clearfix {
      *zoom: 1
  }
  ```

  

* **Unicode编码字体：**

* 把中文字体的名称用相应的Unicode编码来代替，这样就可以有效的避免浏览器解释CSS代码时候出现乱码的问题。比如：
  * 黑体 \9ED1\4F53
  * 宋体 \5B8B\4F53
  * 微软雅黑 \5FAE\8F6F\96C5\9ED1
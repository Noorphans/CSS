

## 效果图

![淘宝焦点图](http://images.newstar.net.cn/sally-imgs%E6%B7%98%E5%AE%9D%E7%84%A6%E7%82%B9%E5%9B%BE.png)



### 布局分析

![1571397019689](http://images.newstar.net.cn/sally-imgs1571397019689.png)

**分析：** 

1. 大盒子我们类名为： tb-promo 淘宝广告

2. 里面先放一张图片。

3. 左右两个按钮 用链接就好了。 左箭头 prev 右箭头 next 

   * 左按钮样式（border-radius：左上，右上，右下，左下）

   * 右按钮定位，提取左右按钮共同的样式代码（并集选择器）

4. 底侧小圆点ul 继续做。 类名为 promo-nav 

   * 中间长方形椭圆 ul的定位（水平居中，离底部15px）  

   * 长方形需要五个小圆点，ul无序列表，li浮动，椭圆中小圆点的样式

```css
<style>
    * {
      margin: 0;
      padding: 0;
    }

    li {
      list-style: none;
    }

    .tb-promo {
      /* 子绝父相 */
      position: relative;
      width: 520px;
      height: 280px;
      background-color: powderblue;
      margin: 100px auto;
    }

    /* 强制规定图片大小，后面图片大一点小一点都没关系 自动拉伸成设置的大小 */
    .tb-promo img {
      width: 520px;
      height: 280px;
    }

    .prev,
    .next {
      position: absolute;
      /* 绝对定位的盒子垂直居中 */
      top: 50%;
      margin-top: -15px;
      /* 加了绝对定位的盒子可以直接设置高度和宽度 */
      width: 20px;
      height: 30px;
      color: #fff;
      background: rgb(0, 0, 0, .4);
      line-height: 30px;
      text-decoration: none;
      text-align: center;
    }

    .prev {
      left: 0;
      /* 圆形 不要这个效果 */
      /* border-radius: 15px; */
      border-top-right-radius: 15px;
      border-bottom-right-radius: 15px;
    }

    .next {
      /* 如果一个盒子既有left属性也有right属性，则默认会执行left属性, 
      同理top和bottom会执行top，所以左右箭头方向分开写，公共部分不写*/
      right: 0;
      border-top-left-radius: 15px;
      border-bottom-left-radius: 15px;
    }

    .promo-nav {
      position: absolute;
      bottom: 15px;
      /* 走70的一半 水平居中 */
      left: 50%;
      margin-left: -35px;
      width: 70px;
      height: 13px;
      /* ul盒子制作 */
      /* background-color: pink; */
      background: rgba(255, 255, 255, .3);
      border-radius: 7px;
    }

    .promo-nav li {
      float: left;
      width: 8px;
      height: 8px;
      background-color: #fff;
      border-radius: 50%;
      margin: 3px;
    }

    /* 不要忘记选择器权重的问题 */
    .promo-nav .selected {
      background-color: #ff5000;
    }
  </style>
</head>

<body>
  <div class="tb-promo">
    <img src="../images/tb.jpg" alt="">
    <!-- 左侧按钮箭头 -->
    <a href="#" class="prev"> &lt; </a>
    <!-- 右侧按钮箭头 -->
    <a href="#" class="next"> &gt; </a>
    <!-- 小圆点 -->
    <ul class="promo-nav">
      <li class="selected"></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
    </ul>
  </div>
</body>
```



> * 如果一个盒子既有left属性也有right属性，则**默认会执行left**属性
> * 同理top和bottom会**执行 top**


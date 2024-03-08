

## 仿土豆网显示隐藏遮罩

### 效果图

![土豆网案例](http://images.newstar.net.cn/sally-imgs%E5%9C%9F%E8%B1%86%E7%BD%91%E6%A1%88%E4%BE%8B.png) 



### 案例目标

1. 练习元素的显示与隐藏

2. 练习元素的定位



### 核心原理

1. 原先半透明的黑色遮罩看不见， 鼠标经过 大盒子，就显示出来。
2. 遮罩的盒子不占有位置， 就需要用绝对定位 和 display  配合使用。



代码参考：

```css
 <style>
    .tudou {
      /* 子绝父相 */
      position: relative;
      width: 444px;
      height: 320px;
      margin: 30px auto;
      background-color: pink;
    }

    /* 图片设置宽高与父盒一样 */
    .tudou img {
      width: 100%;
      height: 100%;
    }

    /* 遮罩层 */
    .mask {
      /* 隐藏遮罩层 */
      display: none;
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0, 0, 0, .4) url(../images/arr.png) no-repeat center;
    }

    /* 当我们鼠标经过了 土豆这个盒子，就让里面遮罩层显示出来 */
    .tudou:hover .mask {
      /*显示元素 */
      display: block;
    }
  </style>
</head>

<body>
  <div class="tudou">
    <div class="mask"></div>
    <img src="../images/tudou.jpg" alt="">
  </div>
  <div class="tudou">
    <div class="mask"></div>
    <img src="../images/tudou.jpg" alt="">
  </div>
</body>
```


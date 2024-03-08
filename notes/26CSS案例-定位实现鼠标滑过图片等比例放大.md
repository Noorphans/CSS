## 需求描述：

​	定位实现鼠标滑过图片等比例放大，显示在原尺寸图片的上方。

### 起始状态

![1571587262015](http://images.newstar.net.cn/sally-imgs1571587262015.png)



### 代码参考

```css
 <style>
    img {
      width: 100px;
      height: 75px;
    }

    .box {
      position: relative;
      width: 600px;
      height: 300px;
      margin: 100px auto;
    }


    .box div {
      /* 每个小盒子在一行显示 宽高值大一些 留足够空间装下图片 */
      float: left;
      width: 106px;
      height: 81px;
      text-align: center;
    }

    /* 当前div被覆盖时，鼠标经过div时，让当前里面的img图片宽、高变大 */
    .box div:hover img {
      /* 子绝父相 */
      position: absolute;
      width: 200px;
      height: 150px;
      margin-top: -25px;
      margin-left: -100px;
    }
  </style>
</head>

<body>
  <div class="box">
    <div><img src="../images/photo/photo01.png"></div>
    <div><img src="../images/photo/photo02.png"></div>
    <div><img src="../images/photo/photo03.png"></div>
    <div><img src="../images/photo/photo04.png"></div>
    <div><img src="../images/photo/photo05.png"></div>
    <div><img src="../images/photo/photo06.png"></div>
    <div><img src="../images/photo/photo07.png"></div>
    <div><img src="../images/photo/photo08.png"></div>
    <div><img src="../images/photo/photo09.png"></div>
    <div><img src="../images/photo/photo10.png"></div>
    <div><img src="../images/photo/photo11.png"></div>
    <div><img src="../images/photo/photo12.png"></div>
    <div><img src="../images/photo/photo13.png"></div>
    <div><img src="../images/photo/photo14.png"></div>
    <div><img src="../images/photo/photo15.png"></div>
    <div><img src="../images/photo/photo16.png"></div>
    <div><img src="../images/photo/photo17.png"></div>
    <div><img src="../images/photo/photo18.png"></div>
    <div><img src="../images/photo/photo19.png"></div>
    <div><img src="../images/photo/photo20.png"></div>
  </div>
</body>
```



### 实现状态

![1571587262015](http://images.newstar.net.cn/sally-imgs%E6%A1%88%E4%BE%8B%E6%95%88%E6%9E%9C.gif)
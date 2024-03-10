[toc]





# CSS 高级技巧

## CSS三角制作

### 介绍

* 网页中**常见一些三角形，使用CSS直接画**出来就可以，不必做成图片或者字体图标。



### 使用 border 属性

```css
<style>
    .box1 {
      width: 0;
      height: 0;
      /* 简写 */
      /* border: 10px solid skyblue; */

      /* 分写 */
      border-top: 10px solid plum;
      border-right: 10px solid papayawhip;
      border-bottom: 10px solid skyblue;
      border-left: 10px solid gray;

    }
  </style>
</head>

<body>
  <div class="box1"></div>
</body>
```

![image-20240309172850919](http://images.newstar.net.cn/sally-imgsimage-20240309172850919.png) 

> 一个盒子没有大小，宽高为0，再给四个不同颜色边框，就会发现每个**`边框本质就是三角形`**



\- 举例：只要一边三角

```css
.box {
      width: 0;
      height: 0;
      margin: 100px auto;
      /* 1. 先全部变为透明色 */
      border: 50px solid transparent;
      /* 2.top为三角 */
      /* border-top-color: plum; */

      /* 3.left为三角 */
      border-top-color: gray;

    }
```



> 1. 4个边框都要写，都改为transparent 透明色，只保留需要的边框颜色，其余的不能省略。
> 2. 为了照顾兼容性 低版本的浏览器，加上font-size: 0;line-height: 0;



![image-20240309192331756](http://images.newstar.net.cn/sally-imgsimage-20240309192331756.png) 



### 放京东三角制作

```css
 <style>
    .box1 {
      position: relative;
      width: 120px;
      height: 249px;
      margin: 100px auto;
      background-color: skyblue;
    }

    span {
      position: absolute;
      right: 15px;
      /* border是5px，那么四个边都是5，下和上是5，top就是10 */
      top: -10px;
      width: 0;
      height: 0;
      font-size: 0;
      line-height: 0;
      border: 5px solid transparent;
      border-bottom-color: skyblue;

    }
  </style>
</head>

<body>
  <div class="box1">仿京东三角制作
    <span></span>
  </div>
</body>
```

![image-20240309195943681](http://images.newstar.net.cn/sally-imgsimage-20240309195943681.png) 


# CSS高级技巧

## 精灵图（重点）

1. 为什么需要精灵图？

2. 精灵图的使用

3. 精灵图课堂案例



### 为什么需要精灵图

![image-20240308103142842](http://images.newstar.net.cn/sally-imgsimage-20240308103142842.png) 

一个网页中往往会应用很多`小背景图像作为修饰`，当网页中的`图像过多`时，服务器就会频繁地接收和发送请求图片，造成`服务器请求压力过大`，这将大大`降低页面的加载速度`。



1. **使用精灵图的目的：** **`为了有效地减少服务器接收和发送请求的次数，提高页面的加载速度`**，出现了`CSS精灵技术`（也称CSS Sprites、 CSS雪碧）。

2. **核心原理**：`将网页中的一些小背景图像整合到一张大图中 ，这样服务器只需要一次请求就可以了`。

3. **精灵图举例**:

![image-20240308103938307](http://images.newstar.net.cn/sally-imgsimage-20240308103938307.png) 



### 精灵图（sprites）的使用

#### 使用精灵图核心

1. `精灵技术主要针对于背景图片使用`。就是把`多个小背景图片合并到一张大图像`中。

   * 这个大图片也称为sprites、精灵图 或者 雪碧图

2. `移动背景图片位置`，此时可以使用`background-position` 。

3. `移动的距离`就是这个`目标图片的x 和 y坐标`。

   * 注意**网页中的坐标有所不同，y轴方向与数学中的定义相反。**

   * 数学中，y轴正方向在上，负方向在下，越往上越大，向下移动y值减少
   * 网页中，y轴正方向在下，负方向在上，越往下越大，向上移动y值减少。
   * 而一般情况下都是`往上往左移动`，所以数值是`负值`。

   ![image-20240308111726507](http://images.newstar.net.cn/sally-imgsimage-20240308111726507.png) 

4. 使用精灵图的时候需要`精确测量`，每个`小背景图片的大小和位置`。





#### 使用精灵图核心总结：

1. 精灵图主要**`针对于小的背景图片`**使用。
2. 主要借助于背景位置来实现---`background-position` 。
3. 一般情况下精灵图都是**`负值`**。

> **千万注意:**网页中坐标,`x`轴`右`边走是`正`值，`左`边走是`负`值，`y`轴同`下`走是`正`值，`上`走是`负`值。



```css
<style>
    .box1 {
      width: 60px;
      height: 60px;
      margin: 100px auto;
      /* 要拿到的是王者荣耀登录的小背景图 所以往左移动  上为0*/
      background: url(../images/sprites.png) -182px 0;
    }

    .box2 {
      width: 25px;
      height: 25px;
      margin: 200px 400px;
      /* background-color: pink; */
      background: url(../images/sprites.png) no-repeat -156px -105px;
    }
  </style>
</head>

<body>
  <div class="box1"></div>
  <div class="box2"></div>
</body>
```





### 案例：拼出自己名字

示例图：

![image-20240308205938370](http://images.newstar.net.cn/sally-imgsimage-20240308205938370.png) 

```css
<style>
    span {
      display: inline-block;
      /* background-color: pink; */
      background: url(../images/abcd.jpg) no-repeat;
    }

    .s {
      width: 115px;
      height: 110px;
      background-position: -252px -420px;
    }

    .a {
      width: 122px;
      height: 111px;
      background-position: 0 -9px;
    }

    .l {
      width: 97px;
      height: 112px;
      background-position: -6px -274px;
    }

    .ll {
      width: 97px;
      height: 112px;
      background-position: -6px -274px;
    }

    .y {
      width: 110px;
      height: 111px;
      background-position: -365px -555px;
    }
  </style>
</head>

<body>
  <span class="s">s</span>
  <span class="a">a</span>
  <span class="l">l</span>
  <span class="ll">l</span>
  <span class="y">y</span>
</body>
```

效果图：

![image-20240308210011909](http://images.newstar.net.cn/sally-imgsimage-20240308210011909.png) 
















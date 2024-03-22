

[toc]



# 移动WEB开发之流式布局



## 移动端技术选型

移动端布局和以前我们学习的PC端有所区别：

![image-20240321195212926](http://images.newstar.net.cn/sally-imgsimage-20240321195212926.png) 



### 流式布局（百分比布局）

* 流式布局，就是百分比布局，也称非固定像素布局。
* 通过盒子的宽度设置成百分比来根据屏幕的宽度来进行伸缩，不受固定像素的限制，内容向两侧填充。
* 流式布局方式是移动web开发使用的比较常见的布局方式。

![image-20240321195358963](http://images.newstar.net.cn/sally-imgsimage-20240321195358963.png) 

* max-width 最大宽度 （max-height 最大高度） 
* min-width 最小宽度 （min-height 最小高度）

```css
 <style>
        * {
            margin: 0;
            padding: 0;
        }
        
        section {
            width: 100%;
            max-width: 980px;
            min-width: 320px;
            margin: 0 auto;
        }
        
        section div {
            float: left;
            width: 50%;
            height: 400px;
        }
        
        section div:nth-child(1) {
            background-color: pink;
        }
        
        section div:nth-child(2) {
            background-color: purple;
        }
    </style>
</head>

<body>
    <section>
        <div></div>
        <div></div>
    </section>
</body>
```

> `320px`是一个`常见的最小宽度`，但在某些情况下，可能会有更小的屏幕尺寸需要考虑。





### 京东移动端首页-案例

#### 技术选型

   * 方案：我们采取单独制作移动页面方案
   * 技术：布局采取流式布局

​    ![image-20240322094706149](http://images.newstar.net.cn/sally-imgsimage-20240322094706149.png)     



#### 搭建相关文件夹结

![image-20240321201203132](http://images.newstar.net.cn/sally-imgsimage-20240321201203132.png) 



#### 设置视口标签以及引入初始化样式

```css
<meta name="viewport" content="width=device-width, user-scalable=no, 
initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
 <link rel="stylesheet" href="css/normalize.css">
 <link rel="stylesheet" href="css/index.css">
```



#### 常用初始化样式

```css
body {
margin: 0 auto;
min-width: 320px;
max-width: 640px;
background: #fff;
font-size: 14px;
font-family: -apple-system, Helvetica, sans-serif;
line-height: 1.5;
color: #666;
}
```



#### 二倍精灵图做法

* 在firework里面把精灵图等比例缩放为原来的一半
* 之后根据大小 测量坐标
* 注意代码里面background-size也要写： 精灵图原来宽度的一半200px 

![image-20240322142714402](http://images.newstar.net.cn/sally-imgsimage-20240322142714402.png) 





#### 图片格式

* DPG图片压缩技术
* webp 图片格式

![image-20240321201507856](http://images.newstar.net.cn/sally-imgsimage-20240321201507856.png) 







## 总结

1. 标准viewport规范以及写法

2. 模拟移动端调试方法

3. 移动端常见的布局方案
4. 流式布局原理

5. 京东移动端首页布局技巧
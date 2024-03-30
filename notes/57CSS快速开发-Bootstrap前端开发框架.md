[toc]



##  Bootstrap 简介

Bootstrap 来自 Twitter（推特），是目前最受欢迎的前端框架。Bootstrap 是基于 HTML、CSS 和 JAVASCRIPT 的，它简洁灵活，**`使得Web开发更加快捷`。**

* 中文官网：**http://www.bootcss.com/**

* 官网：**http://getbootstrap.com/**

* Bootstrap3： https://bootstrap.css88.com/更改为**https://v3.bootcss.com/** 

  

**`框架`：**顾名思义就是一套架构，它有一套比较完整的网页功能解决方案，而且控制权在框架本身，有预制样式库、组件和

插件。使用者要按照框架所规定的某种规范进行开发。

![image-20240328164351904](http://images.newstar.net.cn/sally-imgsimage-20240328164351904.png) 



### 优点

* 标准化的html+css编码规范
* 提供了一套简洁、直观、强悍的组件
* 有自己的生态圈，不断的更新迭代
* 让开发更简单，提高了开发的效率





### 版本

* 2.x.x：停止维护,兼容性好,代码不够简洁，功能不够完善。
* 3.x.x：放弃了 IE6-IE7。对 IE8 支持但是界面效果不好,依赖 jQuery，偏向用于开发响应式布局
* **4.x.x** ：支持 IE10+ 浏览器，支持 Flexbox 布局、不依赖 jQuery
* **5.x.x** ：支持 Flexbox 布局、支持 Grid 布局、支持 CSS 自定义属性、不依赖 jQuery，但是不支持 IE 浏览器



> 本次采用Bootstrap v3版本



## Bootstrap 使用

* 在现阶段我们还没有接触JS相关课程，所以我们只考虑使用它的样式库。

* `控制权在框架本身，使用者要按照框架所规定的某种规范进行开发`

* Bootstrap 使用四步曲：1. 创建文件夹结构 **2. 创建 html 骨架结构** 3. 引入相关样式文件 4. 书写内容

  
  
### 创建文件夹结构

![image-20240328181148474](http://images.newstar.net.cn/sally-imgsimage-20240328181148474.png) 

​     

   

### 创建 html 骨架结构 

  ```css
  <!--要求当前网页使用IE浏览器最高版本的内核来渲染-->
   <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <!--视口的设置：视口的宽度和设备一致，默认的缩放比例和PC端一致，用户不能自行缩放-->
   <meta name="viewport" content="width=device-width, initial-scale=1, user-scalable=0">
   <!--[if lt IE 9]>
   <!--解决ie9以下浏览器对html5新增标签的不识别，并导致CSS不起作用的问题-->
   <script src="https://oss.maxcdn.com/html5shiv/3.7.2/html5shiv.min.js"></script>
   <!--解决ie9以下浏览器对 css3 Media Query 的不识别 -->
   <script src="https://oss.maxcdn.com/respond/1.4.2/respond.min.js"></script>
   <![endif]-->
  ```

  



### 引入相关样式文件 

  ```css
  <!-- Bootstrap 核心样式-->
  <link rel="stylesheet" href="bootstrap/css/bootstrap.min.css">
  ```

​     

### 书写内容

* 直接拿Bootstrap 预先定义好的样式来使用

* 修改Bootstrap 原来的样式，注意**权重**问题

  * 如果自己的样式没有效果，就需要注意权重问题，把权重提高

  * Bootstrap是通过它的类名来控制，只要把它的类名复制过来去修改自己想要的即可，比如想要红色的登录按钮，复制类名即可

  ![image-20240328183759413](http://images.newstar.net.cn/sally-imgsimage-20240328183759413.png)

* 学好Bootstrap 的关键在于知道`它定义了哪些样式，以及这些样式能实现什么样的效果`

 

## 布局容器

* Bootstrap 需要为页面内容和栅格系统包裹一个.container容器，Bootstrap`预`先`定义`好了这个`类`，叫.container，它提供了两个作此用处的类。
* 有了这个 ，就不需要定义不同屏幕下媒体查询的各个档位了
* container-fluid：fluid流式的，类似百分比布局 宽度占百分百



![image-20240328185610696](http://images.newstar.net.cn/sally-imgsimage-20240328185610696.png) 


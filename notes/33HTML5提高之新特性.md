[toc]



# HTML5新特性

## 概述

* `HTML5`的新增特性主要是针对于以前的不足，增加了一些`新的标签、新的表单`和`新的表单属性`等。 

* 这些新特性都有兼容性问题，基本是 **IE9+ 以上版本的浏览器**才支持，如果不考虑兼容性问题，可以大量使用这些新特性。

* 声明：新特性增加了很多，但是我们**专注于开发常用的新特性**。

  

## 新增的语义化标签 （★★）

* 以前布局，我们基本用 div 来做。div对于搜索引擎来说，是没有语义的

```html
<div class=“header”> </div>
<div class=“nav”> </div>
<div class=“content”> </div>
<div class=“footer”> </div>
```

* 发展到了HTML5后，新增了一些语义化标签，这样的话更加有利于浏览器的搜索引擎搜索
* 也方便了网站的seo（Search Engine Optimization，搜索引擎优化），下面就是新增的一些语义化标签
  * `<header>` 头部标签
  * `<nav>` 导航标签
  * `<article>` 内容标签，用于表示独立、完整的内容单元，比如一篇博客文章、一则新闻报道等
  * `<section>` 定义html文档`某个区域`，当做更有语义的div
  * `<aside>` 侧边栏标签
  * `<footer>` 尾部标签

![image-20240311101219654](http://images.newstar.net.cn/sally-imgsimage-20240311101219654.png) 



> **注：**
>
> 1. 这种语义化标准主要是`针对搜索引擎`的
> 2. 这些新标签页面中可以`使用多次`
> 3. 在 `IE9` 中，需要把这些元素`转换为块级元素`
> 4. 其实，我们**移动端更喜欢使用这些标签**(因移动端没有兼容性问题)
> 5. HTML5 还增加了很多其他标签，后面再慢慢学



## 多媒体标签

* 多媒体标签主要分为：`音频 audio` 和`视频 video`两个标签
* 使用它们,可以很方便的在页面中嵌入音频和视频，而不再去使用落后的flash和其他浏览器插件。
* 因为多媒体标签的 属性、方法、事件比较多，因此我们需要什么功能的时候，就需要去查找相关的文档进行学习使用。



### 视频标签- video（★★★）

HTML5 在不使用插件的情况下，也可以原生的支持视频格式文件的播放，当然，支持的格式是有限的

#### 基本使用

当前 **<video>** 元素支持三种视频格式： 尽量使用**mp4格式**

**使用语法：**

```html
 <video src="media/mi.mp4"></video>
```



![video支持格式](http://images.newstar.net.cn/sally-imgsvideo%E6%94%AF%E6%8C%81%E6%A0%BC%E5%BC%8F.png) 



#### 兼容写法(了解)

由于各个浏览器的支持情况不同，所以我们会有一种兼容性的写法，这种写法了解一下即可

```html
<video  controls="controls"  width="300">
    <source src="move.ogg" type="video/ogg" >
    <source src="move.mp4" type="video/mp4" >
    您的浏览器暂不支持 <video> 标签播放视频
</ video >
```

> 上面这种写法，`浏览器会匹配video标签中的source`，如果`支持就播放`，如果不支持往下匹配，`从上往下执行，直到没有匹配的格式，就提示文本`





#### video 常用属性

![video常用属性](http://images.newstar.net.cn/sally-imgsvideo%E5%B8%B8%E7%94%A8%E5%B1%9E%E6%80%A7.png) 

> **需重点掌握的属性：**
>
> 1. `autoplay` 自动播放
>    * 注意： 在google浏览器上面，默认禁止了自动播放，如果想要自动播放的效果，需要设置 muted属性
> 2. `width`宽度、`height`高度、`src`播放源、`muted`静音播放、`loop`循环播放

**示例代码：**

```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>HTML5新增视频标签</title>
    <style>
        video {
            width: 200px;
        }
    </style>
</head>

<body>
    <!-- loop循环播放，muted静音播放 ,poster网速慢的时候显示 加载等待图片-->
    <video src="media/mv.mp4" controls="controls" autoplay="autoplay" loop="loop" muted="muted"
        poster="media/image.png"></video>
</body>
```





### 音频标签- audio

当前 **<audio>** 元素支持三种视频格式： 尽量使用 **mp3格式**

**使用语法：**

```html
<audio src="media/music.mp3"></audio>
```

![](http://images.newstar.net.cn/sally-imgsaudio%E6%94%AF%E6%8C%81%E6%A0%BC%E5%BC%8F.png)



#### 兼容写法(了解)

由于各个浏览器的支持情况不同，所以我们会有一种兼容性的写法

```html
< audio controls="controls"  >
    <source src="happy.mp3" type="audio/mpeg" >
    <source src="happy.ogg" type="audio/ogg" >
    您的浏览器暂不支持 <audio> 标签。
</ audio>
```

> 浏览器会匹配audio标签中的source，如果支持就播放，如果不支持往下匹配，直到没有匹配的格式，就提示文本



#### audio 常用属性

![](http://images.newstar.net.cn/sally-imgsaudio%E5%B8%B8%E7%94%A8%E5%B1%9E%E6%80%A7.png)

**示例代码：**

```html
<audio src="media/music.mp3" autoplay="autoplay" controls="controls"></audio>
```





### 音频&视频小结

- 音频标签和视频标签使用方式基本一致
- 浏览器支持情况不同
- 谷歌浏览器把音频和视频自动播放禁止了,可以给`视频标签添加 muted` 属性来`静音播放`视频，音频不可以（可以通过JavaScript解决）
- `视频标签是重点`，我们`经常设置自动播放`、循环和设置大小属性,`不使用controls控件`





## 新增的表单元素 （★★）

在H5中，帮我们新增加了很多类型的表单，这样方便了程序员的开发





### 常见input输入类型

![image-20240115150653328](http://images.newstar.net.cn/sally-imgsimage-20240115150653328.png)   



### 新增的input输入类型

![image-20240311212020275](http://images.newstar.net.cn/sally-imgsimage-20240311212020275.png) 

> **重点记住：** 现阶段**重点记忆三个**： **`number`   `tel`   `search`**



\- 举例说明:

```html
<!-- 我们验证的时候必须添加form表单域 -->
<form action="">
    <ul>
        <li>邮箱: <input type="email" /></li>
        <li>网址: <input type="url" /></li>
        <li>日期: <input type="date" /></li>
        <li>时间: <input type="time" /></li>
        <li>数量: <input type="number" /></li>
        <li>手机号码: <input type="tel" /></li>
        <li>搜索: <input type="search" /></li>
        <li>颜色: <input type="color" /></li>
        <!-- 当我们点击提交按钮就可以验证表单了 -->
        <li> <input type="submit" value="提交"></li>
    </ul>
</form>
```



![image-20240311210453172](http://images.newstar.net.cn/sally-imgsimage-20240311210453172.png) 





### 新增的表单属性

![image-20240311213131068](http://images.newstar.net.cn/sally-imgsimage-20240311213131068.png) 



**`通过以下设置方式修改placeholder里面的字体颜色`：**

```css
input::placeholder {

 color: pink;

 }
```



代码参考：

```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>HTML5新增表单属性</title>
    <style>
        input::placeholder {
            color: pink;
        }
    </style>
</head>

<body>
    <form action="">
        <input type="search" name="sear" id="" required="required" placeholder="Sally" autofocus="autofocus"
            autocomplete="off">
        <input type="file" name="" id="" multiple="multiple">
        <input type="submit" value="提交">
    </form>
</body>
```






## 携程网首页案例制作

访问地址：m.ctrip.com

![image-20240323110455821](http://images.newstar.net.cn/sally-imgsimage-20240323110455821.png) 



### 技术选型

* 方案：我们采取单独制作移动页面方案
* 技术：布局采取flex布局





### 搭建相关文件夹结构

![image-20240323110701215](http://images.newstar.net.cn/sally-imgsimage-20240323110701215.png) 



### 设置视口标签以及引入初始化样式

```css
<meta name="viewport" content="width=device-width, user-scalable=no, 
initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
 <link rel="stylesheet" href="css/normalize.css">
 <link rel="stylesheet" href="css/index.css">
```





### 常用初始化样式

```css
body {
max-width: 540px;
min-width: 320px;
margin: 0 auto;
font: normal 14px/1.5 Tahoma,"Lucida Grande",Verdana,"Microsoft
Yahei",STXihei,hei;
color: #000;
background: #f2f2f2;
overflow-x: hidden;
-webkit-tap-highlight-color: transparent;
}
```





### 常见模块命名

![image-20240323110918094](http://images.newstar.net.cn/sally-imgsimage-20240323110918094.png) 



![image-20240323110942900](http://images.newstar.net.cn/sally-imgsimage-20240323110942900.png) 



#### 顶部搜索模块

1. 首先给盒子固定定位fixed固定搜索框，固定的盒子应该有宽度，设置宽为100%，高44px
2. 固定定位跟父级没有关系 它以(浏览器窗口)屏幕为准,所以要限制最大和最小宽度
3. 有定位，盒子居中不能用margin：atuo，左先移动一半50%，再移动子盒子自身宽度的一半，但宽度有大有小可缩放，不确定。所以用 transform: translateX(-50%);移动元素自身的一半







###  常见flex布局思路

![image-20240323111017331](http://images.newstar.net.cn/sally-imgsimage-20240323111017331.png) 



##  背景线性渐变

![image-20240323111434771](http://images.newstar.net.cn/sally-imgsimage-20240323111434771.png) 



* 语法：

```css
background: linear-gradient(起始方向, 颜色1, 颜色2, ...);
background: -webkit-linear-gradient(45deg, red , blue);
background: -webkit-linear-gradient(left top, red , blue);
```

> * 背景渐变`必须添加浏览器私有前缀`
> * 起始方向可以是： 方位名词 或者 度数 ， 如果**省略默认就是 top**

 

### 线性渐变-起始方向之方位名词

```css
 /* 1.默认起始位置top，上黄下紫 */
background: -webkit-linear-gradient(yellow, plum);
 /* 2.左黄右紫 */
background: -webkit-linear-gradient(left, yellow, plum); 
/* 3.左上角橘色到右下角绿色的渐变*/
background: -webkit-linear-gradient(left top,orange, green);
```

![image-20240323114613496](http://images.newstar.net.cn/sally-imgsimage-20240323114613496.png) 





### 线性渐变-起始方向之度数

```css
background: -webkit-linear-gradient(135deg, deeppink, orange);
background: -webkit-linear-gradient(270deg, deeppink, orange);
background: -webkit-linear-gradient(45deg, deeppink, orange);
```

![image-20240323120819930](http://images.newstar.net.cn/sally-imgsimage-20240323120819930.png) 





### 线性渐变-复杂示例&透明渐变

1. **复杂渐变**

可以创建更复杂的渐变，包括多个颜色和位置值。位置值指定了渐变的起始和结束位置。

```css
 background: -webkit-linear-gradient(45deg, red 0%, blue 30%, green 70%, yellow 100%);
```

![image-20240323121548803](http://images.newstar.net.cn/sally-imgsimage-20240323121548803.png) 



2. **透明渐变**

```css
background: -webkit-linear-gradient(right, rgba(255, 0, 0, 0.5), rgba(0, 0, 255, 0.5));
```

![image-20240323121925558](http://images.newstar.net.cn/sally-imgsimage-20240323121925558.png) 




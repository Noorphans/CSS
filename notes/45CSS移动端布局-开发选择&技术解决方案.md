[toc]





# 移动WEB开发之流式布局



## 移动端开发选择

### 移动端主流方案

1. **单独制作`移动端`页面（主流）**
   * 京东商城手机版
   * 淘宝触屏版
   * 苏宁易购手机版
2. **`响应式`页面兼容移动端（其次）**
   * 三星手机官网



### 单独制作移动端页面（主流）

通常情况下，网址域名前面加 **`m(mobile)`** 可以打开移动端。通过判断设备，如果是移动设备打开，则跳到**`移动端页面`**。 

![image-20240321191531066](http://images.newstar.net.cn/sally-imgsimage-20240321191531066.png) 





### 响应式兼容PC移动端

* 三星电子官网： www.samsung.com/cn/ ，通过判断屏幕宽度来改变样式，以适应不同终端。 

* **缺点：**`制作麻烦`， 需要花很大精力去调`兼容性`问题

![image-20240321191659331](http://images.newstar.net.cn/sally-imgsimage-20240321191659331.png) 



## 移动端开发选择-总结

> * 现在市场常见的移动端开发有 单独制作移动端页面 和 响应式页面 两种方案
> * 现在市场主流的选择还是`单独制作移动端页面`







## 移动端技术解决方案

* 移动端浏览器基本以 webkit 内核为主，因此我们就考虑webkit兼容性问题。
* 可以放心使用 H5 标签和 CSS3 样式。
* 同时我们浏览器的私有前缀我们只需要考虑添加 webkit 即可

![image-20240321192144899](http://images.newstar.net.cn/sally-imgsimage-20240321192144899.png) 



### CSS初始化 normalize.css

移动端 CSS初始化推荐使用 normalize.css/

* Normalize.css：保护了有价值的默认值
* Normalize.css：修复了浏览器的bug
* Normalize.css：是模块化的
* Normalize.css：拥有详细的文档
* 官网地址： http://necolas.github.io/normalize.css/





### CSS3盒子模型 box-sizing

* 传统模式宽度计算：盒子的宽度 = CSS中设置的width + border + padding 
* CSS3盒子模型：盒子的宽度 = CSS中设置的宽度width 里面包含了border和padding 
* 也就是说，我们的CSS3中的盒子模型， padding 和 border 不会撑大盒子了

```css
 /*CSS3盒子模型*/
 box-sizing: border-box;
 /*传统盒子模型*/
 box-sizing: content-box;
```



#### 如何选择传统盒子模型和CSS3盒子模型

> * `移动端可以全部CSS3盒子模型`
> * PC端如果完全`需要兼容`旧版本浏览器或特定环境，我们就用`传统模式`；如果`不考虑兼容性`，我们就选择`CSS3盒子模型`







### 特殊样式

```css
 /*CSS3盒子模型*/
 box-sizing: border-box;
 -webkit-box-sizing: border-box;

 /*点击高亮我们需要清除清除 设置为transparent 完成透明*/
 -webkit-tap-highlight-color: transparent;

 /*在移动端浏览器默认的外观,即在iOS上加上这个属性才能去掉默认亮光效果，给按钮和输入框自定义样式*/
 -webkit-appearance: none;
 
/*禁用长按页面时的弹出菜单*/
 img,a { -webkit-touch-callout: none; }
```


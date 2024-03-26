[toc]

# 苏宁网首页案例制作



访问地址：m.suning.com





## 技术选型rem适配1

方案：我们采取单独制作移动页面方案

技术：布局采取rem适配布局（less + rem + 媒体查询）

设计图： 本设计图采用 750px 设计尺寸





###  搭建相关文件夹结构

![image-20240324212302865](http://images.newstar.net.cn/sally-imgsimage-20240324212302865.png) 



### 设置视口标签以及引入初始化样式

```css
<meta name="viewport" content="width=device-width, user-scalable=no, 
initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
 <link rel="stylesheet" href="css/normalize.css">
```





### 设置公共common.less文件

1. 新建common.less 设置好最常见的屏幕尺寸，利用媒体查询设置不同的html字体大小，因为除了首页其他页面也需要

2. 我们关心的尺寸有 320px、360px、375px、384px、400px、414px、424px、480px、540px、720px、750px

3. 划分的份数我们定为 15等份

4. 因为我们pc端也可以打开我们苏宁移动端首页，pc端尺寸是非常大的，
   * 比如说是1340，1600px去除以15，那就太大了
   * 我们把html字体大小写死，定为 50px，
   * pc端打开就直接显示50px，就不用除以15了，
   * font-size: 50px; 注意这句话`写到最上面`





### 新建index.less文件

1. 新建index.less 这里面写首页的样式

2. 将刚才设置好的 common.less 引入到index.less里面 语法如下：

```less
// 在 index.less 中导入 common.less 文件
@import “common”
```

3. 生成index.css 引入到 index.html 里面





### body样式

```less
body {
min-width: 320px;
width:15rem;
margin: 0 auto;
line-height: 1.5;
font-family: Arial,Helvetica;
background: #F2F2F2;
}
```







##  技术选型rem适配2

* flexible.js + rem布局
* 手机淘宝团队出的`简洁高效`, **移动端适配库**。再也不需要在写不同屏幕的媒体查询，因为里面js做了处理。
* 它的原理：是把当前设备划分为**10等份**，但是不同设备下，比例还是一致的。
* 我们要做的，就是`确定好当前`设备的`html文字大小`就可以了
* 比如：当前设计稿是 750px
  * 那么我们只需要把 html 文字大小设置为 75px(750px / 10) 就可以
  * 里面页面元素rem值： 页面元素的px 值 / 75 
  * 剩余的，让flexible.js来去算
  * github地址：https://github.com/amfe/lib-flexible



* 方案：我们采取单独制作移动页面方案
* 技术：布局采取rem适配布局2（flexible.js + rem）
* 设计图： 本设计图采用 750px 设计尺寸





###  搭建相关文件夹结构

![image-20240324212302865](http://images.newstar.net.cn/sally-imgsimage-20240324212302865.png) 



### 设置视口标签以及 引入初始化样式&js文件

```css
<meta name="viewport" content="width=device-width, user-scalable=no, 
initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
<link rel="stylesheet" href="css/normalize.css">
<link rel="stylesheet" href="css/index.css">
```

* 在index.html页面中 引入flexible.js 这个文件

```html
<script src=“js/flexible.js”> </script>
```





###  body样式

```css
body {
min-width: 320px;
width:15rem;
margin: 0 auto;
line-height: 1.5;
font-family: Arial,Helvetica;
background: #F2F2F2;
}
```





## VSCode之px转换rem的插件cssrem

> 这个插件默认的html文字大小,根元素cssroot 为16px，即1rem等于16px，需要**根据所选尺寸**设置扩展里**手动更改**

* 因为选的是750px尺寸的，那么1rem应该等于75px，因为flexible划分了10等份

* `手动更改设置html字体大小基准值`

  1. 打开 设置搜索cssrem 找到Cssrem：Root Font Size并修改
  2. 设置html字体大小基准值

  ![image-20240326200257517](http://images.newstar.net.cn/sally-imgsimage-20240326200257517.png) 

![image-20240326200747057](http://images.newstar.net.cn/sally-imgsimage-20240326200747057.png)  
[toc]



> 本次采用Bootstrap v3版本

##   栅格系统简介

* **`栅格系统`**英文为“grid systems”,采取格子的方式进行布局
* 也有人翻译为“网格系统”,网格布局，它是指将**页面布局**划分为`等宽的列`，然后**通过列数的定义来模块化**页面布局。
* Bootstrap 提供了一套响应式、移动设备优先的流式栅格系统，随着屏幕或视口（viewport）尺寸的增加，系统会将**页面内容**自动分为最多**`12列`**。
  * 也就是说小屏幕和大屏幕下都是12列
  * 响应式里必须有个container父盒子，所以说栅格系统是把container划分为12等份

> **注:** 栅格系统是将 **页面内容**划分为若干**等宽的列**，rem是划分整个屏幕的份数





## 栅格选项参数

栅格系统用于通过一系列的行（row）与列（column）的组合来创建页面布局，你的内容就可以放入这些创建好的布局中。

![image-20240328192902261](http://images.newstar.net.cn/sally-imgsimage-20240328192902261.png) 

* 行(row)必须放到container布局容器里面
* 我们实现列的平均划分 需要给**列**添加`类前缀`
* 按照不同屏幕划分为1~12 等份
* 行（row） 可以去除父容器作用15px的边距
* xs-extra small：超小； sm-small：小； md-medium：中等； lg-large：大；
* 列（column）大于 12，多余的“列（column）”所在的元素将被作为一个整体另起一行排列
* 每一列默认有左右15像素的 padding
* 可以同时为一列指定多个设备的类名，以便划分不同份数 例如 class="col-md-4 col-sm-6"



* 代码示例：

```html
 <div class="container">
        <!-- 
            大屏幕下4个盒子，每个盒子占3份
            中屏幕下3个盒子，每个盒子占4分
            小屏幕下2个盒子，每个盒子占2份
         -->
        <div class="row">
            <div class="col-lg-3 col-md-4 col-sm-6 col-xs-12">1</div>
            <div class="col-lg-3 col-md-4 col-sm-6 col-xs-12">2</div>
            <div class="col-lg-3 col-md-4 col-sm-6 col-xs-12">3</div>
            <div class="col-lg-3 col-md-4 col-sm-6 col-xs-12">4</div>
        </div>
        <!-- 如果孩子的份数相加等于12 则孩子能占满整个的container 的宽度 -->
        <div class="row">
            <div class="col-lg-6">1</div>
            <div class="col-lg-2">2</div>
            <div class="col-lg-2">3</div>
            <div class="col-lg-2">4</div>
        </div>
        <!-- 如果孩子的份数相加小于 12 则会？ 则占不满整个container的宽度 会有空白 -->
        <div class="row">
            <div class="col-lg-6">1</div>
            <div class="col-lg-2">2</div>
            <div class="col-lg-2">3</div>
            <div class="col-lg-1">4</div>
        </div>
        <!-- 如果孩子的份数相加 大于 12 则会？多于的那一列会 另起一行显示  -->
        <div class="row">
            <div class="col-lg-6">1</div>
            <div class="col-lg-2">2</div>
            <div class="col-lg-2">3</div>
            <div class="col-lg-3">4</div>
        </div>

    </div>
```







##  列嵌套

* 栅格系统内置的栅格系统将内容再次嵌套。
* 简单理解：就是**一个列内**`再分`成**若干份小列**。我们可以通过添加一个新的.row 元素和一系列 .col-sm-* 元素到已经存在的 .col-sm-* 元素内。

![image-20240328200157788](http://images.newstar.net.cn/sally-imgsimage-20240328200157788.png) 

```html
<!-- 列嵌套 -->
 <div class="col-sm-4">
 <div class="row">
 <div class="col-sm-6">小列</div>
 <div class="col-sm-6">小列</div>
 </div>
</div>
```

> **注：** 列嵌套最好`加1个row` 这样可以`取消父元素的padding值`,而且`高度自动和父级一样高`



## 列偏移

* 使用 .col-md-offset-* 类可以将列向右侧偏移。这里的*代表偏移的列数
* 这些类实际是通过使用偏移 为当前元素 增加了左侧的边距（margin）。

![image-20240328200641215](http://images.newstar.net.cn/sally-imgsimage-20240328200641215.png) 

![image-20240328195842645](http://images.newstar.net.cn/sally-imgsimage-20240328195842645.png) 

* 想让左侧盒子贴向左边，右侧盒子贴向右侧，中间为空
  * 不能用margin值，响应式布局宽度是自适应的，不知道具体距离
  * 使用列偏移，向右偏移

```html
 <!-- 列偏移 -->
 <div class="row">
 <!-- 偏移的份数= 12 减去 两个盒子的份数8 = 4 -->
 <div class="col-lg-4">1</div>
 <div class="col-lg-4 col-lg-offset-4">2</div>
 </div>

<!-- 如果只有一个盒子在中间 那么就偏移 = (12 - 6) /2 -->
  <div class="row">
   <div class="col-md-6 col-md-offset-3">中间盒子</div>
   </div>
```

> 中间留白，两边盒子贴边：偏移的份数= 12- 两个盒子的份数
>
> 一个盒子居中：偏移的份数= (12 减去 一个盒子份数)/2







##  列排序

通过使用 (推送).col-md-push-* 和 (拉取) .col-md-pull-* 类就可以很容易的**改变列**（column）的**顺序**

![image-20240328210554994](http://images.newstar.net.cn/sally-imgsimage-20240328210554994.png) 

> **改变列顺序：** 先拉后推

```html
 <!-- 列排序 -->
 <div class="row">
 <div class="col-lg-4 col-lg-push-8">左侧</div>
 <div class="col-lg-8 col-lg-pull-4">右侧</div>
 </div>
```







## 响应式工具

为了加快对移动设备友好的页面开发工作，利用媒体查询功能，并使用这些工具类可以方便的针对**不同设备展示或隐藏页面内容**

![image-20240328211418755](http://images.newstar.net.cn/sally-imgsimage-20240328211418755.png) 

* 与之相反的，是visible-xs 、visible-sm、visible-md、visible-lg是显示某个页面内容

```html
<body>
    <div class="container">
        <div class="row">
            <div class="col-xs-3">
                <span class="visible-lg">我只在大屏幕下显示哦</span>
            </div>
            <div class="col-xs-3">2</div>
            <div class="col-xs-3  hidden-md hidden-xs">我只在中屏幕和超小屏幕下隐藏</div>
            <div class="col-xs-3">4</div>
        </div>

    </div>
</body>
```





> Bootstrap 其他（按钮、表单、表格） 请参考[Bootstrap 文档](https://v4.bootcss.com/docs/getting-started/introduction/)
[toc]



## CSS的背景

* 通过 CSS **背景属性**，可以给页面元素添加背景样式。
* 背景属性可以设置**背景颜色**、**背景图片**、**背景平铺**、**背景图片位置**、**背景图像固定**等



### 背景颜色

* `background-color`属性定义了元素的背景颜色

![image-20240124135115033](http://images.newstar.net.cn/sally-imgsimage-20240124135115033.png) 

* 一般情况下元素背景颜色`默认值`是 `transparent`（透明），不写也是默认transparent
* 如果想给某个盒子改为透明的，也可以用`transparent手动指定`背景颜色为`透明色`

![image-20240124141016193](http://images.newstar.net.cn/sally-imgsimage-20240124141016193.png) 







### 背景图片

* 目标：能够写出背景图片的设置方式

* `background-image`属性描述了元素的背景图像。实际开发常见于logo或者一些装饰性的小图片或者是超大的背景图片, 优点是非常便于控制位置. (精灵图也是一种运用场景)

 ![image-20240124140914013](http://images.newstar.net.cn/sally-imgsimage-20240124140914013.png) 

![image-20240124141259798](http://images.newstar.net.cn/sally-imgsimage-20240124141259798.png) 

> **注意：**背景图片后面的`地址`，千万不要忘记**`加 URL`**， 同时里面的**`路径不要加引号`**。



\- 举例说明：

```html
 <style>
    div {
      width: 200px;
      height: 200px;
       /* 添加背景图片 */  
      background-image: url(../images/pic.jpeg);
    }
  </style>
</head>

<body>
  <div></div>
</body>
```









### 背景平铺

如果需要在 HTML 页面上**对背景图像进行平铺**，可以使用 `background-repeat`属性。

 ![1570886648887](http://images.newstar.net.cn/sally-imgs1570886648887.png)



![1570886684882](http://images.newstar.net.cn/sally-imgs1570886684882.png) 

> **注：**`背景图片默认都是平铺的`





#### 完全平铺repeat

* 就是把一张图像像拼贴一样重复放置，以覆盖需要填充的区域

```html
<style>
    div {
      /* 设置相等的宽高或者特定比例可以确保图片在调整大小时保持正确的外观 */
      width: 300px;
      height: 300px;
      /* 添加背景图片 */
      background-image: url(../images/logo.png);

      /* 1.背景图片默认都是平铺的 */
      /* background-repeat: repeat; */
    }
  </style>
</head>

<body>
  <div></div>
</body>
```



 ![image-20240124145936050](http://images.newstar.net.cn/sally-imgsimage-20240124145936050.png)







#### 不平铺no-repeat

* 整个背景区域只会`显示一张图片`的单个实例，不进行复制和重复填充。

```html
<style>
    div {
      /* 设置相等的宽高或者特定比例可以确保图片在调整大小时保持正确的外观 */
      width: 300px;
      height: 300px;
      /* 添加背景图片 */
      background-image: url(../images/logo.png);

     /* 2.背景图片不平铺 */
      background-repeat: no-repeat;

    }
  </style>
</head>

<body>
  <div></div>
</body>
```

![image-20240124150744847](http://images.newstar.net.cn/sally-imgsimage-20240124150744847.png) 







#### 横向平铺repeat-x

* 图片沿着**水平方向**进行复制，填满整个横向区域。(左右连接在一起，形成一个无缝的`横向延伸`的图案。)

```html
<style>
    div {
      /* 设置相等的宽高或者特定比例可以确保图片在调整大小时保持正确的外观 */
      width: 300px;
      height: 300px;
      /* 添加背景图片 */
      background-image: url(../images/logo.png);

    /* 3.沿着x轴 横向平铺 */
    background-repeat: repeat-x;

    }
  </style>
</head>

<body>
  <div></div>
</body>
```

![image-20240124150848982](http://images.newstar.net.cn/sally-imgsimage-20240124150848982.png) 







#### 纵向平铺repeat-y

* 也叫垂直平铺： 图片沿着垂直方向进行复制，填满整个纵向区域。(顶部和底部连接在一起，形成一个无缝的`纵向延伸`的图案。)

```html
<style>
    div {
      /* 设置相等的宽高或者特定比例可以确保图片在调整大小时保持正确的外观 */
      width: 300px;
      height: 300px;
      /* 添加背景图片 */
      background-image: url(../images/logo.png);

     /* 沿着y轴 纵向平铺 */
      background-repeat: repeat-y;

    }
  </style>
</head>

<body>
  <div></div>
</body>
```

![image-20240124143902018](http://images.newstar.net.cn/sally-imgsimage-20240124143902018.png) 

> **注：** *可以添加背景颜色也可以添加背景图片 只不过背景颜色被压在底部*







## 背景图片位置(非常重要)

* 利用 `background-position`属性可以改变图片在背景中的位置。

![image-20240124151849804](http://images.newstar.net.cn/sally-imgsimage-20240124151849804.png) 

* 参数代表的意思是：x坐标和 y坐标。可以使用 **`方位名词`** 或者 **`精确单位`**

![image-20240124152045508](http://images.newstar.net.cn/sally-imgsimage-20240124152045508.png) 





###  参数是方位名词

> 如果指定的两个值都是方位名词，则两个值**`前后顺序无关`**，比如 `left top` 和 `top left` **效果一致**

* 比如，设置图片靠上对齐 水平居中显示

```html
 <style>
    div {
      width: 300px;
      height: 300px;
      background-image: url(../images/logo.png);
      background-color: plum;
      background-repeat: no-repeat;

      /* 方位名词background-position */
      background-position: center top;

    }
  </style>
</head>

<body>
  <div></div>
</body>
```

![image-20240124152936785](http://images.newstar.net.cn/sally-imgsimage-20240124152936785.png) 

* 比如,水平靠右对齐显示

```html
<style>
    div {
      width: 300px;
      height: 300px;
      background-image: url(../images/logo.png);
      background-color: plum;
      background-repeat: no-repeat;

      /* 方位名词background-position  */
      /* 水平靠右对齐  center right也可以*/
      background-position: right center;
    }
  </style>
</head>

<body>
  <div></div>
</body>
```

![image-20240124153342897](http://images.newstar.net.cn/sally-imgsimage-20240124153342897.png) 









> **注：**
>
> * 通常情况`第一个值`表示`水平方向`x轴，`第二个值`表示`垂直方向`y轴，如只提供一个方位名词，浏览器会根据默认规则来确定水平方向的位置。
>
> * 简单理解：提供一个方位名词，另一个值被省略且默认居中对齐
>
>   1. 如果**只指定一个方位名词**为：**left 、right或center**
>      * `第一个值`为水平方向`x轴`.而`省略第二个值`，即`y轴`垂直方向默认 `垂直居中`(center)
>
>   2. 如果**只指定一个方位名词**为：**top、bottom**
>      * `第一个值`为垂直方向`y轴`.而`省略第二个值`，即`x轴`水平方向默认 `水平居中`(center)
>      * **因为只有y轴才有top、bottom值**

\- 举例说明：

```html
<style>
    div {
      width: 300px;
      height: 300px;
      background-image: url(../images/logo.png);
      background-color: plum;
      background-repeat: no-repeat;

      
      /* 指定一个方位名词  此时，水平一定是靠左对齐，第二个参数省略 即y轴是垂直居中显示的*/
      /* background-position: left; */

      /* 指定一个方位名词  此时，第一个值一定是top y轴顶部对齐，第二个参数省略 即x轴是水平居中显示的*/
      background-position: top;
        
       /* 水平垂直居中 一个center和两个一样效果 */
      background-position: center;  
    }
  </style>
</head>

<body>
  <div></div>
</body>
```

![image-20240124185146987](http://images.newstar.net.cn/sally-imgsimage-20240124185146987.png) 

![image-20240124185209197](http://images.newstar.net.cn/sally-imgsimage-20240124185209197.png) 

![image-20240124185125326](http://images.newstar.net.cn/sally-imgsimage-20240124185125326.png) 









### 参数是精确单位

> 如果参数值是**精确坐标**，那么`第一个肯定是 x 坐标`，`第二个一定是 y 坐标`(**有严格顺序**)
>
> * 比如：background-position: 20px 50px; (x轴一定是20， y轴一定是50)

\- 举例说明：

```html
 <style>
    div {
      width: 300px;
      height: 300px;
      background-color: pink;
      background-image: url(../images/logo.png);
      background-repeat: no-repeat;

      /* x轴一定是20， y轴一定是50*/
      background-position: 20px 50px;
    }
  </style>
</head>

<body>
  <div></div>
</body>
```

![image-20240125160952568](http://images.newstar.net.cn/sally-imgsimage-20240125160952568.png) 









> 如果只**指定一个数值**，那`该数值一定是 x 坐标`，`另一个`**默认垂直居中**

\- 举例说明：

```html
<style>
    div {
      width: 300px;
      height: 300px;
      background-color: pink;
      background-image: url(../images/logo.png);
      background-repeat: no-repeat;

      /* 指定一个数 一定是x轴 20px ，第二个默认垂直居中*/
      background-position: 20px;
    }
  </style>
</head>

<body>
  <div></div>
</body>
```











### 参数是混合单位

> 如果指定的两个值是`精确单位和方位名词混合使用`，则`第一个值是 x 坐标`，`第二个值是 y 坐标`(**有严格顺序**)
>
> * 比如： background-position: center 20px; (第一个是x轴 center水平居中 ，第二个垂直20px)

```html
<style>
    div {
      width: 300px;
      height: 300px;
      background-color: pink;
      background-image: url(../images/logo.png);
      background-repeat: no-repeat;

      /* 第一个一定是x轴 center水平居中 ，第二个垂直20px*/
      background-position: center 20px;
    }
  </style>
</head>

<body>
  <div></div>
</body>
```









## 背景图片固定

* 也称背景附着：`background-attachment` 属性设置`背景图像是否固定或者随着页面`的其余部分`滚动`。
* background-attachment 后期可以制作视差滚动的效果

![image-20240125163812891](http://images.newstar.net.cn/sally-imgsimage-20240125163812891.png) 

![image-20240125163848767](http://images.newstar.net.cn/sally-imgsimage-20240125163848767.png) 



\- 举例说明：

```html
<style>
    body {
      background-image: url(../images/bg1.jpg);
      background-repeat: no-repeat;
      background-position: top;
      color: plum;
      font-size: 20px;

      /* 固定图片 只滚动内容 */
      background-attachment: fixed;

    }
  </style>
</head>

<body>
  <p>王者荣耀出新皮肤啦</p>
  <p>王者荣耀出新皮肤啦</p>
  <p>王者荣耀出新皮肤啦</p>
  <p>王者荣耀出新皮肤啦</p>
  <p>王者荣耀出新皮肤啦</p>
  <p>王者荣耀出新皮肤啦</p>
  <p>王者荣耀出新皮肤啦</p>
  <p>王者荣耀出新皮肤啦</p>
</body>
```

> **注：** 背景图片 默认是随着页面内容滚动的 scroll









## 背景属性复合写法

* 为了简化背景属性的代码，我们可以将这些属性**合并简写**在同一个属性`background`中。从而节约代码量.

* 实际开发中，我们更提倡的写法如下，当使用简写属性时，没有特定的书写顺序,一般`习惯约定顺序`为：

  * `background:背景颜色、背景图片、背景平铺、背景图像滚动、背景图片位置`

  ![image-20240125194629616](C:\Users\Sally\AppData\Roaming\Typora\typora-user-images\image-20240125194629616.png) 

  ```css
  <style>
      body {
        /* background: transparent url(../images/logo.png) no-repeat fixed right 80px; */
        background: gray url(../images/bg.jpg) no-repeat fixed center top;
      }
    </style>
  ```

  > 属性之间空格隔开 和 font字体属性简写一样

 







## 背景色半透明

CSS3 为我们提供了背景颜色半透明的效果

![image-20240125200152368](C:\Users\Sally\AppData\Roaming\Typora\typora-user-images\image-20240125200152368.png)  

> **注：**
>
> 1. `rgba`---->`red、 green、 blue 、alpha`
> 2. `最后一个参数`是 alpha `透明度`，取值范围在 `0~1之间`
> 3. 我们`习惯`把 0.3 的 `0 省略掉`，写为 **`background: rgba(0, 0, 0, .3);`**
> 4. 注意：背景半透明是指盒子背景半透明，盒子里面的内容不受影响
> 5. CSS3 新增属性，是 IE9+ 版本浏览器才支持的，现在实际开发,我们不太关注兼容性写法了,可以放心使用



\- 举例说明：

```html
<style>
    div {
      width: 300px;
      height: 300px;
      background: rgba(99, 182, 182, .1);
    }
  </style>
</head>

<body>
  <div>隐形的翅膀</div>
</body>
```

![image-20240125200424282](C:\Users\Sally\AppData\Roaming\Typora\typora-user-images\image-20240125200424282.png) 











## 背景总结

![1570888283511](E:\学习资料\HTML+CSS\基础部分\04-前端基础CSS第二天\笔记\images\1570888283511.png)

> 1. **背景图片**:实际开发**常见于logo**或者一些**装饰性的小图片**或者是**超大的背景图片**, 优点是非常便于控制位置. (精灵图也是一种运用场景)
> 2. **背景颜色**：同笔记-04CSS文本外观属性之颜色
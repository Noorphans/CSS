[toc]



# flex布局父项常见属性





* 以下由6个属性是对父元素设置的:
  1. flex-direction：设置主轴的方向
  2. justify-content：设置主轴上的子元素排列方式
  3. flex-wrap：设置子元素是否换行 
  4. align-content：设置侧轴上的子元素的排列方式（多行）
  5. align-items：设置侧轴上的子元素排列方式（单行）
  6. flex-flow：复合属性，相当于同时设置了 flex-direction 和 flex-wrap







## flex-direction设置主轴的方向(重点)

在`flex布局中`，是分为`主轴和侧轴`两个方向，同样的叫法有：`行和列、x轴和y轴`



### 主轴与侧轴

* 默认`主轴`方向就是`x轴`方向，`水平向右(行)`
* 默认`侧轴`方向就是`y轴`方向，`水平向下(列)`

![image-20240322195441158](http://images.newstar.net.cn/sally-imgsimage-20240322195441158.png) 



### flex-direction的属性值(牢记)

`flex-direction`属性`决定主轴方向`（即**项目的排列方向**）

> **注意：** 主轴和侧轴是会变化的，**默认主轴是x轴，(行)从左到右**。`就看flex-direction设置谁为主轴`，**剩下的就是侧轴**。而我们的`子元素是跟着主轴来排列的`



* **重点记住**:  **`row & column`**

![image-20240322200014367](http://images.newstar.net.cn/sally-imgsimage-20240322200014367.png) 



\- 举例说明：

```css
 div {
            /* 1.给父级添加flex属性 */
            display: flex;
            width: 800px;
            height: 300px;
            background-color: pink;
            /* 1. 默认的主轴是 x 轴为行 row ，从左到右 那么y轴就是侧轴 */
            /* 我们的元素是跟着主轴来排列的 */
            /* flex-direction: row; */

            /* 2. 从右到左，翻转 简单了解即可*/
            /* flex-direction: row-reverse; */

            /* 我们可以把我们的主轴设置为 y轴，那么x轴就成了侧轴 */
            flex-direction: column;
        }

        div span {
            width: 150px;
            height: 100px;
            background-color: plum;
        }
    </style>
</head>

<body>
    <div>
        <span>1</span>
        <span>2</span>
        <span>3</span>
    </div>
</body>
```

![image-20240322201259733](http://images.newstar.net.cn/sally-imgsimage-20240322201259733.png) 





## justify-content设置主轴上的子元素排列方式

justify-content属性 定义了项目在主轴上的对齐方式

> **注意：** `使用这个属性之前一定要确定好主轴是哪个`





* **重点记住**: **`space-between`**

![image-20240322202403013](http://images.newstar.net.cn/sally-imgsimage-20240322202403013.png)  





##  flex-wrap设置子元素是否换行

默认情况下，项目都排在一条线（又称”轴线”）上。flex-wrap属性定义，flex布局中`默认是不换行`的。 



* **重点记住**: **`flex-wrap换行`**

![image-20240322203806307](http://images.newstar.net.cn/sally-imgsimage-20240322203806307.png) 





## align-items设置侧轴上的子元素排列方式（单行 ）

该属性是`控制子项在侧轴`（默认是y轴）上的排列方式 在`子项为单项（单行）`的时候使用,也就是只有一行的时候



* **重点记住：** **`flex-start、center`**

![image-20240322204257888](http://images.newstar.net.cn/sally-imgsimage-20240322204257888.png)  

> **align-items: stretch;** `默认拉伸`, 前提是`子盒子不要给高度`才看得出效果







## align-content设置侧轴上的子元素的排列方式（多行）

设置子项在侧轴上的排列方式 并且只能用于`子项出现换行`的情况（多行），在单行下是没有效果的

![image-20240322205810621](http://images.newstar.net.cn/sally-imgsimage-20240322205810621.png) 





## align-content 和 align-items 区别

* align-items 适用于单行情况下， 只有上对齐、下对齐、居中和 拉伸
* align-content 适应于`换行`（多行）的情况下（单行情况下无效）， 可以设置 上对齐、 下对齐、居中、拉伸以及平均分配剩余空间等属性值。

> 总结就是:**单行找 align-items ,多行找align-content**



![image-20240322210430294](http://images.newstar.net.cn/sally-imgsimage-20240322210430294.png) 





## flex-flow属性

* flex-flow属性是 flex-direction 和 flex-wrap 属性的复合属性
* 语法：

```css
flex-flow:row wrap;
```



\- 举例说明：

```css
   <style>
        div {
            display: flex;
            width: 600px;
            height: 300px;
            background-color: pink;
            /* 分写 */
            /* flex-direction: column;
            flex-wrap: wrap; */

            /* 简写：把设置主轴方向和是否换行（换列）简写 */
            flex-flow: column wrap;
        }

        div span {
            width: 150px;
            height: 100px;
            background-color: purple;
        }
    </style>
</head>

<body>
    <div>
        <span>1</span>
        <span>2</span>
        <span>3</span>
        <span>4</span>
        <span>5</span>
    </div>
</body>
```







## 总结

* flex-direction：设置主轴的方向
* justify-content：设置主轴上的子元素排列方式
* flex-wrap：设置子元素是否换行 
* align-content：设置侧轴上的子元素的排列方式（多行）
* align-items：设置侧轴上的子元素排列方式（单行）
* flex-flow：复合属性，相当于同时设置了 flex-direction 和 flex-wrap


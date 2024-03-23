[toc]



# flex布局子项常见属性



* flex 子项目占的份数
* align-self 控制子项自己在侧轴的排列方式
* order属性定义子项的排列顺序（前后顺序）





## flex 属性(重点)

* flex属性:定义子项目分配剩余空间，用flex来表示占多少`份数`。
* number可以是正数(扩展分配剩余空间)、百分比(基于父元素的宽度 扩展分配剩余空间)
* 语法：

```css
.item {
 flex: <number>; /* 默认default 0  */
}
```



\- 举例说明：京东首页搜索框布局

* CSS样式

```css
<style>
        /* 京东首页搜索框布局 */
        section {
            display: flex;
            width: 60%;
            height: 150px;
            margin: 0 auto;
            background-color: pink;
        }

        section div:nth-child(1) {
            width: 100px;
            height: 150px;
            background-color: plum;
        }

        section div:nth-child(2) {
            /* flex分配剩余空间 数字1 分一份，默认是0*/
            flex: 1;
            background-color: gainsboro;
        }

        section div:nth-child(3) {
            width: 100px;
            height: 150px;
            background-color: skyblue;
        }
    </style>
```



* HTML结构

```html
  <section>
        <div></div>
        <div></div>
        <div></div>
    </section>
```

![image-20240323102307160](http://images.newstar.net.cn/sally-imgsimage-20240323102307160.png) 







##  align-self控制子项自己在侧轴上的排列方式

* align-self属性:`允许单个项目`**有不一样的对齐方式**，**可覆盖align-items**属性。
  * `默认`值为`auto`，表示`继承父元素的align-items属性`，如果`没有父元素`或`父元素未设置`align-items属性，则等同于`stretch`。
* 语法：

```css
span:nth-child(2) {
 /* 设置自己在侧轴上的排列方式 */
 align-self: flex-end;
 }
```



\- 举例说明：

* 只让3号盒子下来底侧

```css
 <style>
        div {
            display: flex;
            width: 80%;
            height: 300px;
            background-color: pink;
            /* 默认主轴X， 侧轴就是y，让三个子盒子沿着侧轴底侧对齐 */
            /* align-items: flex-end; */
        }

        div span {
            width: 150px;
            height: 100px;
            background-color: purple;
            margin-right: 5px;
        }

        div span:nth-child(3) {
            /* 我们想只让3号盒子下来底侧 */
            align-self: flex-end;
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

![image-20240323103536633](http://images.newstar.net.cn/sally-imgsimage-20240323103536633.png) 





## order属性定义项目的排列顺序

* 数值`越小`，排列`越靠前`，**默认为0**。
* 注意：**和 z-index 不一样**。

```css
.item {
 order: <number>;
}
```



\- 举例说明：

```css
 <style>
        div {
            display: flex;
            width: 80%;
            height: 300px;
            background-color: pink;
            /* 默认主轴X， 侧轴就是y，让三个子盒子沿着侧轴底侧对齐 */
            /* align-items: flex-end; */
        }

        div span {
            width: 150px;
            height: 100px;
            background-color: purple;
            margin-right: 5px;
        }

        div span:nth-child(2) {
            /* 默认是0   -1比0小所以在前面 */
            order: -1; 
        }
		
		div span:nth-child(3) {
            /* 默认是0   -3比-1小所以在前面 */
             order: -3; 
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

![image-20240323105654572](http://images.newstar.net.cn/sally-imgsimage-20240323105654572.png) 
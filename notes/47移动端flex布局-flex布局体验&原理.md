[toc]





##  传统布局与flex布局的区别

![image-20240322191051784](http://images.newstar.net.cn/sally-imgsimage-20240322191051784.png)

**建议：**

> * 如果是`PC端页面`布局，我们还是`传统布局`。
> * 如果是`移动端`或者`不考虑兼容性问题的PC端页面布局`，我们还是使用`flex弹性布局`





## flex布局体验

* 如下，大盒子里包含三个小盒子并且有宽高，显示在一行
  1. 以前做法：给三个盒子指定大小后，添加浮动和清除浮动
  2. flex布局：span直接给宽高度，背景颜色，还有蓝色边框，div只需要添加 “display：flex” 即可

   ![image-20240322191751379](http://images.newstar.net.cn/sally-imgsimage-20240322191751379.png) 



### 搭建HTML结构

```html
 <div>
 <span>1</span>
 <span>2</span>
 <span>3</span>
 </div>
```

* 里面的3个span是行内元素

> **注：** 
>
> 1. flex布局，在行内元素里也可以布局。
> 2. 用`flex布局`，都`可设置大小`，`不需要转换模式`。不分行内元素块元素等显示模式等

```css
 <style>
        div {
            display: flex;
            width: 80%;
            height: 200px;
            background-color: pink;
            
            justify-content: space-around;
        }

        div span {
            /* width: 150px; */
            height: 100px;
            background-color: plum;
            margin-right: 5px;
            flex: 1;
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







## flex弹性布局原理(重点)

1. flex是flexible Box的缩写，意为"弹性布局"，用来为盒状模型提供最大的灵活性，`任何一个容器都可以指定为flex布局。`
   * 当我们为**`父盒子设为flex`**布局以后，**子元素的float、clear 和 vertical-align 属性将失效**,`子元素会自动按照Flex 容器的排列方向进行布局`,它本身就可以把盒子放在一行显示,哪怕指定大小。
   * 伸缩布局 = 弹性布局 = 伸缩盒布局 = 弹性盒布局 =flex布局
2. `采用Flex布局的元素`，称为**Flex容器**（flex container），简称"容器"。它的`所有子元素自动成为容器成员`，称为**Flex项目**（flex item），简称"项目"。
   * 体验中 div 就是 flex父容器。
   * 体验中 span 就是 子容器 flex项目
   * 子容器可以横向排列也可以纵向排列

<img src="http://images.newstar.net.cn/sally-imgsimage-20240322194342352.png" alt="image-20240322194342352" style="zoom:80%;" /> 



> **`总结flex布局原理：`** 
>
> * 就是通过给**`父盒子添加flex属性`**，来`控制子盒子的位置和排列方式`
> * 父元素添加flex，子元素是行内元素 可以直接设置宽高





